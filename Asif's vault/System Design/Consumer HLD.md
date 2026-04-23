# High-Level Design (HLD)


![[HLDMDRevamp.png]]
## Market Data Ingestion, Ordering, and Persistence Service

This design leverages Spring’s dependency injection to decouple component lifecycle management from runtime execution and threading concerns. All core components—including the routing layer, ordered executor services, and market data processors—are instantiated as singleton Spring beans with application-wide lifecycles. JMS listener threads serve purely as invocation contexts that trigger routing logic and submit work for asynchronous execution, but do not create, own, or manage any system components. This separation ensures thread safety, enables deterministic ordering guarantees, and allows concurrency to be controlled explicitly through executor policies rather than implicit thread coupling.

---

## 1. Purpose & Scope

This document describes the high-level architecture of a **market data ingestion service** responsible for consuming market data from a Solace JMS queue, enforcing deterministic ordering guarantees, and persisting market data curves into a database.

The system is designed to support:

- Multiple market data types (e.g., forwards, vol surfaces, correlation curves, PCA shocks)
    
- Concurrent processing where safe
    
- Strict sequential processing where required
    
- High throughput under bursty market conditions
    
- Deterministic and auditable behavior suitable for trading and risk systems
    

This document focuses on **architectural structure and responsibilities**, not implementation details.

---

## 2. Non-Goals

The following are explicitly out of scope for this HLD:

- Curve construction mathematics
    
- Pricing, valuation, or risk calculations
    
- Database schema design
    
- Deployment topology
    
- Exact Solace configuration
    
- Monitoring, alerting, or SLAs
    

---

## 3. Architectural Principles

The system is built around the following core principles:

1. **Type-agnostic ingestion**  
    Message consumption is decoupled from market data semantics.
    
2. **Business-defined ordering guarantees**  
    Ordering is enforced based on business identity, not technical attributes.
    
3. **Stateless processing**  
    All processors are singleton and stateless to ensure thread safety and scalability.
    
4. **Asynchronous, event-driven execution**  
    Ingestion, routing, and processing are decoupled to avoid blocking.
    
5. **Centralized lifecycle control**  
    Message acknowledgement and failure handling are owned by a single orchestration layer.
    
6. **Correctness over theoretical maximum parallelism**  
    Deterministic behavior is prioritized over unsafe concurrency.
    

---

## 4. High-Level Architecture Overview

At a high level, the system consists of the following layers:

1. Message Ingestion Layer
    
2. Routing & Ordering Layer
    
3. Processing Layer
    
4. Persistence Layer
    

Each layer has clearly defined responsibilities and explicit boundaries.

---

## 5. Message Ingestion Layer

### 5.1 Responsibilities

The Message Ingestion Layer is responsible for:

- Listening to a Solace JMS queue
    
- Receiving messages concurrently
    
- Parsing messages into a common envelope format
    
- Performing basic structural validation
    
- Handing off messages for downstream processing
    

### 5.2 Characteristics

- Implemented using **generic, multi-threaded JMS listeners**
    
- Completely **type-agnostic**
    
- Contains **no business logic**
    
- Does **not** enforce ordering
    
- Does **not** perform acknowledgements
    

### 5.3 Key Design Intent

This layer exists solely to absorb incoming traffic efficiently and hand messages off as quickly as possible.

---

## 6. Message Envelope

All incoming messages are normalized into a common **Market Data Envelope**.

### 6.1 Envelope Contents

Each envelope contains:

- Market data type
    
- Deterministic ordering key
    
- As-of / effective date
    
- Version or sequence metadata
    
- Payload
    

### 6.2 Ordering Key

The ordering key:

- Is derived from business identifiers
    
- Uniquely identifies a logical market data object (e.g., a curve)
    
- Remains stable across updates
    
- Is independent of message arrival time or version
    

Ordering guarantees rely on both broker-level message grouping and application-level ordered execution. Messages sharing the same ordering key are published with the same Solace message group ID, ensuring that subsequent versions are not delivered until prior versions are acknowledged. In addition, the application enforces sequential execution per ordering key via single-threaded processing lanes. This dual-layer approach prevents version inversion and ensures that newer market data cannot be overwritten by older versions, even under failure and redelivery scenarios.
---

## 7. Routing & Ordering Layer

### 7.1 Responsibilities

The Routing & Ordering Layer is the **orchestration core** of the system. It is responsible for:

- Extracting the ordering key from each message
    
- Selecting the appropriate processing lane
    
- Selecting the appropriate market data processor
    
- Coordinating execution and completion
    
- Owning message acknowledgement decisions
    

### 7.2 Processing Lanes

- The system maintains a fixed number of **single-threaded processing lanes**
    
- Each lane processes tasks sequentially
    
- Lanes are selected using a deterministic hash of the ordering key
    

### 7.3 Ordering Model

- Messages with the same ordering key always map to the same lane
    
- Messages in the same lane are processed strictly sequentially
    
- Messages with different ordering keys may execute in parallel
    
- A single lane may process multiple market data types
    

Ordering is enforced **before** any business logic is executed.

**To prevent starvation of ordered message groups, failures are classified as recoverable or non-recoverable. Recoverable failures result in message redelivery and preserve ordering by blocking subsequent messages. Non-recoverable (poison) messages are explicitly routed to a dead-letter queue and acknowledged, allowing subsequent versions for the same ordering key to proceed. This approach preserves deterministic ordering while ensuring system liveness and operational visibility.**

---

## 8. Processing Layer

### 8.1 Market Data Processors

Market data processing is implemented using **type-specific processors**.

Each processor:

- Supports exactly one market data type
    
- Is a Spring singleton
    
- Is stateless
    
- Contains only business logic
    

### 8.2 Processor Responsibilities

Processors are responsible for:

- Business-level validation
    
- Mapping payloads to domain objects
    
- Persisting market data curves to the database
    
- Throwing typed exceptions on failure
    

Processors:

- Do not manage threads
    
- Do not acknowledge messages
    
- Do not perform retries
    
- Do not enforce ordering
    

---

## 9. Persistence Layer

### 9.1 Responsibilities

The Persistence Layer:

- Stores market data curves in a relational database
    
- Provides durability and consistency
    
- Acts as the primary throughput bottleneck
    

### 9.2 Design Assumptions

- Database write latency dominates end-to-end processing time
    
- Ordering at the application level reduces contention
    
- The persistence model is compatible with idempotent updates
    

---

## 10. Acknowledgement & Failure Handling

### 10.1 Acknowledgement Ownership

- Message acknowledgement is owned by the **Routing & Ordering Layer**
    
- Acknowledgement occurs **only after successful processing**
    
- Processors never acknowledge messages
    

### 10.2 Failure Semantics

- Recoverable failures result in no acknowledgement and message redelivery
    
- Non-recoverable failures result in dead-letter routing and acknowledgement
    
- Ordering lanes naturally block subsequent messages until the current message resolves
    

---

## 11. Concurrency Model

### 11.1 Ingestion Concurrency

- JMS listener threads are used to absorb bursts
    
- Listener threads never block on processing
    

### 11.2 Processing Concurrency

- Parallelism is achieved across processing lanes
    
- Sequential execution is enforced within a lane
    
- Hot market data objects naturally serialize
    

---

## 12. End-to-End Flow

```json
Solace Queue    
		↓
Generic JMS Listener Pool   
		↓ 
Envelope Parsing & Validation   
		↓ 
Ordering Key Extraction    
		↓ 
Lane Selection (Hash-Based)   
		↓ 
Single-Threaded Processing Lane    
		↓ 
Type-Specific Stateless Processor    
		↓ 
Database Persistence    
		↓ 
Message Acknowledgement
```

---

## 13. Scalability & Extensibility

Adding a new market data type requires:

- Defining a new ordering key format
    
- Implementing a new processor
    

No changes are required to:

- JMS listeners
    
- Ordering logic
    
- Threading model
    
- Acknowledgement flow
    

---

## 14. Key Architectural Guarantees

The system guarantees:

- Deterministic ordering per market data object
    
- At-least-once processing semantics
    
- Stateless and thread-safe processing
    
- Controlled concurrency
    
- Predictable failure behavior