# Low-Level Design (LLD)

## Market Data Ingestion, Ordering, and Processing System

---

## 1. Design Goals

The low-level design aims to:

- Preserve strict ordering per market data object
    
- Enable high concurrency without synchronization
    
- Keep components stateless, composable, and testable
    
- Centralize lifecycle concerns (ack, retry, DLQ)
    
- Allow easy extension for new market data types
    
- Make correctness _structural_, not accidental
    

---

## 2. Core Abstractions Overview

|Component|Responsibility|SOLID Principle|
|---|---|---|
|`MarketDataListener`|Message ingestion|SRP|
|`MarketDataRouter`|Orchestration & routing|SRP|
|`OrderingExecutor`|Ordered execution|SRP|
|`MarketDataProcessor`|Business logic|SRP, OCP|
|`ProcessorRegistry`|Processor resolution|DIP|
|`ProcessingTask`|Command wrapper|Command Pattern|
|`FailureClassifier`|Failure semantics|SRP|
|`AcknowledgementHandler`|Ack & DLQ|SRP|

---

## 3. Message Ingestion Layer

### 3.1 `MarketDataListener`

```java
@Component
public class MarketDataListener {

    private final MarketDataRouter router;

    public MarketDataListener(MarketDataRouter router) {
        this.router = router;
    }

    @JmsListener(destination = "MARKET.DATA.QUEUE")
    public void onMessage(Message message) {
        MarketDataEnvelope envelope = EnvelopeParser.parse(message);
        router.route(envelope, message);
    }
}

```

``

#### Design Notes

- **SRP**: Only message ingestion
    
- **DIP**: Depends on `MarketDataRouter` abstraction
    
- No business logic
    
- No acknowledgement
    
- No threading
    

---

## 4. Routing & Ordering Layer

### 4.1 `MarketDataRouter` (Orchestrator)

```java
@Component
public class MarketDataRouter {

    private final OrderingExecutor orderingExecutor;
    private final ProcessorRegistry processorRegistry;
    private final FailureHandler failureHandler;

    public void route(MarketDataEnvelope envelope, Message message) {
        MarketDataProcessor processor =
            processorRegistry.get(envelope.getDataType());

        ProcessingTask task =
            new ProcessingTask(envelope, message, processor, failureHandler);

        orderingExecutor.submit(envelope.getOrderingKey(), task);
    }
}

```

#### Design Patterns

- **Command Pattern** (`ProcessingTask`)
    
- **Strategy Pattern** (`MarketDataProcessor`)
    
- **Template Method** (inside task execution)
    

#### SOLID

- **SRP**: Routing + orchestration only
    
- **OCP**: New processors without modification
    
- **DIP**: Depends on interfaces
    

---

## 5. Ordered Execution Layer

### 5.1 `OrderingExecutor`

```java
@Component
public class OrderingExecutor {

    private final ExecutorService[] lanes;

    public void submit(String orderingKey, Runnable task) {
        int lane = Math.abs(orderingKey.hashCode() % lanes.length);
        lanes[lane].submit(task);
    }
}

```

#### Key Properties

- Single-threaded lanes
    
- No locks
    
- No shared mutable state
    
- Structural ordering guarantee
    

#### SOLID

- **SRP**: Execution ordering only
    
- **ISP**: Minimal interface
    

---

## 6. Processing Command (Critical Component)

### 6.1 `ProcessingTask` (Command Pattern)

```java
public class ProcessingTask implements Runnable {

    private final MarketDataEnvelope envelope;
    private final Message message;
    private final MarketDataProcessor processor;
    private final FailureHandler failureHandler;

    @Override
    public void run() {
        try {
            processor.process(envelope);
            message.acknowledge();
        } catch (Exception ex) {
            failureHandler.handle(ex, envelope, message);
        }
    }
}

```

#### Why This Is Important

- Encapsulates **execution + callbacks**
    
- Preserves ordering (runs inside lane)
    
- Centralizes ack logic
    
- No blocking
    
- No futures
    

---

## 7. Processing Layer

### 7.1 `MarketDataProcessor` (Strategy Interface)

```java
public interface MarketDataProcessor {
    MarketDataType supports();
    void process(MarketDataEnvelope envelope);
}
```

#### SOLID

- **OCP**: New processors via extension
    
- **LSP**: All processors interchangeable
    
- **ISP**: Minimal contract
    

---

### 7.2 Concrete Processor Example

```java
@Component
public class ForwardCurveProcessor implements MarketDataProcessor {

    private final ForwardCurveRepository repository;

    @Override
    public void process(MarketDataEnvelope envelope) {
        ForwardCurve curve = mapper.map(envelope);
        repository.save(curve);
    }
}

```

#### Design Rules

- Stateless
    
- No threading
    
- No ack
    
- No retries
    
- No ordering logic
    

---

## 8. Processor Registry

### 8.1 `ProcessorRegistry` (Factory + Registry)

```java
@Component
public class ProcessorRegistry {

    private final Map<MarketDataType, MarketDataProcessor> processors;

    public MarketDataProcessor get(MarketDataType type) {
        return processors.get(type);
    }
}
```

#### Design Patterns

- **Factory Pattern**
    
- **Registry Pattern**
    

#### SOLID

- **DIP**: Router depends on abstraction
    
- **OCP**: New processors auto-registered
    

---

## 9. Failure Handling

### 9.1 Failure Classification

```java
public interface FailureHandler {
    void handle(Exception ex,
                MarketDataEnvelope envelope,
                Message message);
}
```

---

### 9.2 Default Failure Handler

```java
@Component
public class DefaultFailureHandler implements FailureHandler {

    @Override
    public void handle(Exception ex,
                       MarketDataEnvelope envelope,
                       Message message) {

        if (ex instanceof RecoverableException) {
            throw ex; // no ack → retry
        }

        if (ex instanceof NonRecoverableException) {
            sendToDlq(envelope, ex);
            message.acknowledge();
        }
    }
}
```

#### Design Notes

- Prevents poison-message starvation
    
- Explicit semantics
    
- Centralized policy
    

---

## 10. Persistence Layer (Version Safety)

### 10.1 Repository Contract

```java
public interface ForwardCurveRepository {
    void save(ForwardCurve curve);
}
```

### 10.2 Version-Safe Implementation

`UPDATE forward_curve SET value = ?, version = ? WHERE curve_id = ?   AND version < ?;`

#### Guarantees

- No pre-read
    
- Atomic
    
- Idempotent
    
- Replay-safe
    

---

## 11. SOLID Principles Summary

|Principle|How It’s Applied|
|---|---|
|SRP|Each class has one reason to change|
|OCP|New data types via extension|
|LSP|Processors interchangeable|
|ISP|Minimal interfaces|
|DIP|High-level logic depends on abstractions|

---

## 12. Design Patterns Used

| Pattern              | Where                 |
| -------------------- | --------------------- |
| Strategy             | `MarketDataProcessor` |
| Command              | `ProcessingTask`      |
| Factory              | `ProcessorRegistry`   |
| Template Method      | Task execution flow   |
| Registry             | Processor lookup      |
| Inversion of Control | Spring DI             |