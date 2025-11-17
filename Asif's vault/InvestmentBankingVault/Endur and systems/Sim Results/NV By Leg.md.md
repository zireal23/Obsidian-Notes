## 🧠 **NV By Leg — Explanation**

### **Definition**

**NV by Leg (Result ID 106)** stands for **Notional Value by Leg**.  
It represents the _monetary value_ of the position or flow **per leg** of a transaction, in the **deal currency**.

In essence:

> It’s the **value of the deal’s physical quantity × price**, expressed in currency terms, for each leg.

---

### **Purpose**

This result provides the **currency valuation** of the underlying quantity for each leg, which can then be reused by other results (like _Current Physical Equiv_, _Projected Physical Equiv_, _Total Physical Equiv_, etc.) to translate physical flows into monetary terms.

---

### **How It’s Computed**

The logic depends on the deal type (Commodity, Power, etc.), but conceptually:

NV by Leg=Quantity by Leg×Price by Leg×Conversion Factors (if any)\text{NV by Leg} = \text{Quantity by Leg} × \text{Price by Leg} × \text{Conversion Factors (if any)}NV by Leg=Quantity by Leg×Price by Leg×Conversion Factors (if any)

Key components:

- **Quantity by Leg** → From the physical or derivative leg of the deal.
    
- **Price by Leg** → From the fixed/floating price terms (could be from market curves, formulas, or indices).
    
- **Conversion factors / UOM scaling** → Applied if the price and quantity use different units (e.g., MWh vs. kWh, or bbl vs. gal).
    
- **FX rate** → Applied if necessary to bring values into the _deal currency_.
    

---

### **Behavior by Deal Type**

|Deal Type|NV by Leg Represents|
|---|---|
|**Physical Commodity**|Value of the physical quantity × contract price (e.g., 10,000 MMBtu × $2.50 = $25,000).|
|**Swap / Forward / Future**|Mark-to-market notional value per leg — typically one leg will be positive (receive leg), another negative (pay leg).|
|**Complex Structured Deals**|Each leg’s NV reflects its standalone notional exposure, which gets summed at the deal level.|

---

### **Result Class & Usage**

- **Result ID:** 106
    
- **Result Enumeration:** `NV_BY_LEG_RESULT`
    
- **Result Class:** `Tran Result`
    
- **Used By:**
    
    - Current Physical Equiv (#43)
        
    - Projected Physical Equiv (#44)
        
    - Other valuation results that convert physical flow → monetary value.
        

---

### **Example**

**Deal:**  
Buy 10,000 MMBtu Gas @ $3.00/MMBtu (delivery in June, pay on July 5)  
Deal currency = USD.

Then for each leg:

- **Quantity by Leg:** +10,000
    
- **Price by Leg:** 3.00
    
- **NV by Leg:** 10,000 × 3.00 = **30,000 USD**
    

On **5th July**, the simulation picks up:

- **Current Physical Equiv (#43):** 30,000 (since it’s now payable)
    
- **Current Physical (#42):** 10,000
    
- **NV by Leg (#106):** 30,000 (used to translate #42 into #43).
    

---

## 🗒️ **Obsidian Note — NV By Leg (Result ID 106)**

**Definition:**  
Represents the notional value of the transaction per leg — i.e., the currency equivalent of the physical quantity and price.

**Formula (conceptual):**

NV by Leg=Quantity by Leg×Price by Leg×FX / Unit Conversions\text{NV by Leg} = \text{Quantity by Leg} × \text{Price by Leg} × \text{FX / Unit Conversions}NV by Leg=Quantity by Leg×Price by Leg×FX / Unit Conversions

**Result Class:** Tran Result  
**Result Enumeration:** NV_BY_LEG_RESULT  
**Used By:** Physical Equiv results (#43, #44, #45)

**Purpose:**  
Provides the base currency valuation per leg so that other results can derive current/projected/total physical equivalents.

**Example:**  
For a 10,000 MMBtu gas deal @ $3.00/MMBtu → NV by Leg = 30,000 USD.