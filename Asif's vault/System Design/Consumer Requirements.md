The consumer must:

1. Consume persistent messages from a Solace queue
    
2. Process messages in parallel
    
3. Parse batched market data deterministically
    
4. Enforce batch atomicity (all-or-nothing)
    
5. Enforce ordering / freshness (no stale overwrites)
    
6. Persist data safely under concurrency
    
7. Be correct under redelivery and restarts

High-Level Consumer Architecture

```
                  Solace Queue
                        |
            +---------------------------+
            | Spring JMS Listener       |
            | (Parallel Consumers)      |
            +---------------------------+
                        |
                  Message Handler
                        |
        +--------------------------------------+
        | Batch Validation & Parsing Layer    |
        | (Stateless Singleton Parsers)       |
        +--------------------------------------+
                        |
              Ordering / Freshness Check
          (Persisted Last-Update State)
                        |
           Conditional Batch Persistence
               (Single DB Transaction)
                        |
                    Database

```

## 3. Parallel Listener Model

### Listener Characteristics

- Multiple JMS listeners run in parallel
    
- Each listener:
    
    - Receives **one message at a time**
        
    - Operates fully independently
        
- No shared in-memory state across listeners
    

### Key Rule

> **Parallelism improves throughput but does not define correctness.**

Correctness is enforced downstream via persistence semantics.

---

## 4. Message Handling Flow (Step-by-Step)

### Step 1: Message Receipt

- Listener receives a persistent JMS message
    
- Message includes:
    
    - `marketDataType`
        
    - `publisherTimestamp`
        
    - Header row
        
    - CSV-encoded rows (100–200)
        

No acknowledgment yet.

---

### Step 2: Market Data Type Dispatch

- Consumer inspects `marketDataType`
    
- Routes message to the appropriate parser
    
- Unsupported types:
    
    - Logged
        
    - Acknowledged
        
    - Dropped
        

---

## 5. Batch Parsing & Validation

### Parsing Rules

- Parser is:
    
    - Singleton
        
    - Stateless
        
    - Thread-safe
        
- Parser:
    
    - Reads header
        
    - Maps CSV fields positionally
        
    - Parses all rows into in-memory structures
        

### Validation Rules (Batch-Wide)

- All rows must:
    
    - Match header column count
        
    - Contain no empty values
        
    - Contain valid numeric/text values
        

### Failure Semantics

- If **any row fails**:
    
    - Entire batch fails
        
    - No DB interaction
        
    - Message is acknowledged (or routed to DLQ)
        

This prevents poison loops.

## 6. Ordering & Freshness Enforcement

### Persisted Ordering State

The database maintains:

`(marketDataType, marketIdentifier) → lastUpdatedTimestamp`

This is the **ordering authority**.

---

### Ordering Decision Logic

For the incoming batch timestamp `T_in`:

|Condition|Action|
|---|---|
|T_in > T_db|Accept batch|
|T_in == T_db|No-op (idempotent)|
|T_in < T_db|Reject batch (stale)|

This decision happens **inside the DB transaction**.

## 7. Transaction Boundary (Critical)

Each message is processed in **one DB transaction** that includes:

1. Read current `lastUpdatedTimestamp`
    
2. Compare with incoming timestamp
    
3. Conditionally persist batch data
    
4. Update `lastUpdatedTimestamp`
    

### Atomic Outcomes

- Either:
    
    - Batch data + timestamp update commit together
        
- Or:
    
    - Nothing is persisted
        

No partial state is possible.

---

## 8. Concurrency Safety

### What Happens Under Parallel Consumers?

- Multiple listeners may process the same index simultaneously
    
- DB enforces:
    
    - Monotonic timestamp progression
        
    - Conditional updates
        

### Result

- Newer data always wins
    
- Older data is safely discarded
    
- No locks, no coordination
    

---

## 9. JMS Acknowledgment Strategy

### Acknowledgment Timing

- Message is acknowledged **only after**:
    
    - Parsing succeeds
        
    - DB transaction completes successfully
        

### Behavior Matrix

|Scenario|ACK?|Result|
|---|---|---|
|Successful persist|✅|Done|
|Stale batch|✅|Done|
|Duplicate batch|✅|Done|
|DB failure|❌|Redelivery|

---

## 10. Redelivery Semantics

Redelivered messages are safe because:

- Parsing is deterministic
    
- Persistence is idempotent
    
- Ordering logic prevents regressions
    

Redelivery does **not** cause data corruption.

---

## 11. Observability Hooks

The consumer emits metrics for:

- Batches processed
    
- Batches rejected (stale / invalid)
    
- Processing latency
    
- Redelivery count
    
- Latest timestamp per index
    

This is essential for operational confidence.

---

## 14. Scalability Characteristics

### Horizontal Scaling

- Add more consumer instances
    
- Increase listener concurrency
    
- No configuration change needed upstream
    

### Bottleneck Location

- Database becomes the natural choke point
    
- Which is **correct** for ordered state
    

---

## 14. Key Design Properties

✔ Correct under concurrency  
✔ Correct under redelivery  
✔ Batch-atomic  
✔ Ordering enforced centrally  
✔ Publisher remains dumb  
✔ Consumers are elastic

