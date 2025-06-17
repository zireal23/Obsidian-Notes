
---
### 🎯 1. **Profitability (P&L) and Spread**

Traders evaluate the **expected P&L**:

- **For client trades**:
    
    - Price offered to the client vs. internal market/hedge price
        
    - Is there a **positive spread**?
        
- **For proprietary trades** (less common in banks post-Volcker):
    
    - What is the directional view on the commodity?
        

💡 **Example (Oil Forward):**  
If a client wants to buy oil at $85/bbl in 3 months, and the trader can hedge this at $84.50, the **$0.50 spread** is profit — assuming no adverse basis/risk.

---

### 📉 2. **Risk Exposure**

Even if profitable, is the **risk acceptable**?

Traders assess:

- **Market risk**: Price movement before hedge is completed (basis risk)
    
- **Credit risk**: Can the counterparty default?
    
- **Liquidity risk**: Can the trade be hedged or exited?
    
- **Operational risk**: Delivery/logistics risks if physical
    

📊 In Endur:

- Simulations may run **Value at Risk (VaR)**, **P&L at Risk**, or stress scenarios.
    
- Credit exposure shown per counterparty.
    

---

### 🧮 3. **Hedgeability**

> Can this trade be hedged **immediately and effectively**?

Traders hate being “naked” (unhedged). They consider:

- Is there a **liquid instrument** to hedge this exposure?
    
- Is the **forward curve** liquid at this maturity?
    
- Are there **storage or logistics constraints**?
    

💡 Example:

- A gas forward at an illiquid location? Harder to hedge.
    
- Might use basis swaps or pipeline capacity to create a hedge.
    

---

### 🤝 4. **Client Relationship / Strategic Fit**

Sometimes a trade is done:

- To **deepen a client relationship**
    
- To **gain future business**
    
- As part of a **structured transaction**
    

The trader might accept lower (or even negative) margins if:

- The client is a **key strategic account**
    
- The overall portfolio benefits
    
- The deal is **part of a larger structured solution**
    

---

### 📉 5. **Regulatory / Capital Cost**

Some trades are expensive **from a capital allocation** perspective:

- Forward contracts can have **collateral or capital requirements**
    
- Trades that increase **wrong-way risk** with a counterparty may be avoided
    
- Regulatory rules (e.g. Basel III) may penalize certain exposures
    

---

### 🛠️ 6. **Analytics and Tools Used**

|Tool|Purpose|
|---|---|
|**Pricing tools**|See curves, vols, implied rates|
|**Endur Simulations**|MTM, VaR, Greeks, cash flows|
|**Curve Viewer (Endur)**|Check curve shape, distortions|
|**Deal Templates**|Compare with similar trades|
|**Trade Capture Risk Preview**|Run pre-deal checks|

---

## ✅ Quick Checklist for "Is This Trade Worth Doing?"

| Question                            | Consideration                         |
| ----------------------------------- | ------------------------------------- |
| What's the P&L/spread?              | Positive expected margin?             |
| Can I hedge it easily?              | Liquidity of hedge market?            |
| What risk does it add?              | VaR / scenario shock impact           |
| Does it fit my position?            | Adds diversification or doubles risk? |
| What’s the credit risk?             | Counterparty limits? Collateralized?  |
| Does this help client relationship? | Future volumes, stickiness            |
| Any capital impact?                 | High margin/collateral burden?        |
Deal Capture
   ↓
Validation & Approval
   ↓
Risk & P&L Simulation
   ↓
Hedging (if required)
   ↓
Operations Setup (for physical)
   ↓
Settlement & Invoicing
   ↓
Accounting
   ↓
Actualization & Deal Closure
