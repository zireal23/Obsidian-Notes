## **Level 0 – Foundational Mental Models**

### **Module 0: Commodities & ETRM – Core Mental Models**

**Objective**  
Establish a common conceptual foundation for understanding commodities trading and ETRM systems.

**Key Topics**

- Commodities vs financial instruments
    
- Physical constraints: time, location, quality, and delivery
    
- Optionality as a source of value
    
- Event-driven vs transaction-driven systems
    
- Why ETRM systems model lifecycle rather than trades alone
    

**Business Perspective**

- Commodities trading is driven by uncertainty and constraints, not just price movement.
    
- Most value is created through managing optionality rather than predicting prices.
    

**System Perspective**

- Why trades decompose into legs, profiles, and events
    
- Why lifecycle events matter more than static data
    
- How Endur mirrors business uncertainty through configuration
    

**Learning Outcome**  
Participants develop an intuition for why ETRM systems are complex and why that complexity is necessary.

---

## **Level 1 – Commodity Business Lifecycle**

# **Level 1 – Participant Brief**

### _Instruments, Participants & Risk in Context_

## Purpose of Level 1

Level 1 is designed to build an **intuitive, end-to-end understanding** of commodities trading by starting from **what is actually traded** and tracing how that flows through:

- Market participants
    
- The value chain
    
- Risk
    
- Pricing
    
- Risk management
    
- System representation (conceptual)
    

---

## How Level 1 Is Structured (Vertical Model)

Each presentation must follow the **same vertical flow**:

1. **Commodity / Instrument**
    
2. **Who Uses It (Participants & Value Chain)**
    
3. **What Risks It Carries**
    
4. **How It Is Priced**
    
5. **How Risk Is Managed (High-Level)**
    
6. **How It Is Represented in Systems (Conceptual)**
    

This structure ensures coherence across all sessions.

---

## What You Will Be Assigned

You will be assigned **one commodity or instrument type** (for example: gas physical contracts, power futures, storage agreements, swing contracts, etc.).

Your job is to explain:

- Why this instrument exists
    
- Who uses it
    
- What problems it solves
    
- What risks it introduces
    

---

## What to Cover (Required)

### 1. Commodity / Instrument

- What is it?
    
- Is it physical, financial, or hybrid?
    
- Why does this instrument exist in the first place?
    

---

### 2. Participants & Value Chain

- Who typically uses this instrument?
    
    - Producers
        
    - Consumers
        
    - Merchants / traders
        
    - Infrastructure players
        
- Where does it sit in:
    
    - Upstream
        
    - Midstream
        
    - Downstream
        

---

### 3. Risk Embedded in the Instrument

Identify the **key risks** carried by this instrument:

- Price risk
    
- Volume risk
    
- Timing risk
    
- Basis / location risk
    
- Operational risk
    

Who wants to eliminate these risks?  
Who is willing to take them?

---

### 4. Pricing & Market Data

- How is this instrument priced?
    
    - Spot
        
    - Forward
        
    - Index-linked
        
    - Formula-based
        
- What market data is required?
    
- Why is pricing non-trivial?
    


---

### 5. Risk Management (High-Level)

- How is the risk observed or controlled?
    
- What is typically measured?
    
- Why risk cannot be fully eliminated
    

⚠️ No calculations required — focus on intuition.

---

### 6. System Representation (Conceptual)

At a **very high level**, explain:

- Why systems need to model this instrument carefully
    
- What business concepts must exist (entities, contracts, portfolios, internal flows)
    
- No configuration or screenshots required

---

## **Level 2 – Risk, Exposure & Performance**

### **Module 4: Risk Management Fundamentals**

**Objective**  
Explain how risk is identified, measured, and controlled in commodities businesses.

**Key Topics**

- Market, credit, liquidity, and operational risk
    
- Exposure vs realized outcomes
    
- Position limits and risk limits
    
- Scenario-based thinking
    

**Business Perspective**

- Risk management exists to prevent catastrophic loss, not to optimize profit.
    
- Risk metrics are approximations of reality.
    

**System Perspective**

- Exposure calculation engines
    
- Aggregation across dimensions (time, location, product)
    
- Limit monitoring and breach workflows
    

**Learning Outcome**  
Participants can reconcile why traders, risk managers, and systems view the same position differently.

---

### **Module 5: PnL, Valuation & Performance Explain**

**Objective**  
Clarify how value is measured and reported across time.

**Key Topics**

- Realized vs unrealized PnL
    
- Mark-to-market valuation
    
- Accruals and timing effects
    
- PnL explain components
    

**Business Perspective**

- PnL volatility does not equal business performance.
    
- Timing mismatches between trading, delivery, and cash are normal.
    

**System Perspective**

- Revaluation mechanics
    
- Event-driven PnL recognition
    
- Explainability of PnL movements
    

**Learning Outcome**  
Participants can interpret PnL beyond surface-level numbers.

---

## **Level 3 – Operations & Financial Reality**

### **Module 6: Physical Operations & Logistics**

**Objective**  
Demonstrate how physical execution impacts commercial outcomes.

**Key Topics**

- Scheduling and nominations
    
- Inventory management
    
- Losses, gains, and adjustments
    
- Actual vs planned volumes
    

**Business Perspective**

- Physical execution determines whether commercial value is realized.
    
- Small operational deviations can have large financial impact.
    

**System Perspective**

- Delivery tracking
    
- Actualization processes
    
- Inventory position updates
    

**Learning Outcome**  
Participants appreciate operations as a value-preserving function, not a back-office activity.

---

### **Module 7: Settlements, Accounting & Financial Controls**

**Objective**  
Explain how trades ultimately translate into cash and financial statements.

**Key Topics**

- Invoicing and settlements
    
- Payment timing and netting
    
- Reconciliation and audit requirements
    

**Business Perspective**

- Financial accuracy protects organizational credibility.
    
- Controls exist to manage regulatory and audit risk.
    

**System Perspective**

- Cash flow generation
    
- Settlement instructions
    
- Accounting events and ledger integration
    

**Learning Outcome**  
Participants understand why finance requirements shape upstream data rigor.

---

## **Level 4 – Organizational Perspectives & Governance**

### **Module 8: Cross-Functional Incentives & Tensions**

**Objective**  
Build empathy for different functional priorities within the organization.

**Key Topics**

- Front office speed vs control
    
- Risk transparency vs commercial flexibility
    
- Operations feasibility vs trading creativity
    
- Finance accuracy vs system agility
    
- IT stability vs business change
    

**System Perspective**

- Endur as a convergence and negotiation point
    
- Configuration as governance
    
- Trade-offs inherent in system design
    

**Learning Outcome**  
Participants understand organizational friction as structural rather than personal.

---

## **Level 5 – Systems Thinking & Change Impact**

### **Module 9: ETRM System Design & Change Management**

**Objective**  
Enable participants to reason about system change holistically.

**Key Topics**

- Endur data model philosophy
    
- Event-driven processing
    
- Configuration vs customization
    
- Impact analysis across modules
    

**Business Perspective**

- Systems encode business assumptions.
    
- Poorly understood changes introduce hidden risk.
    

**System Perspective**

- Dependency chains
    
- Lifecycle impacts of configuration changes
    
- Upgrade and regression risk
    

**Learning Outcome**  
Participants develop a systems-level mindset, anticipating downstream consequences before implementing change.