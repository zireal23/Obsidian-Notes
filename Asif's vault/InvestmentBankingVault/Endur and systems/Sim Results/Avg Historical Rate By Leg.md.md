## 🔎 Avg Hist By Leg Result (Result ID 117)

### What it represents

- **Purpose**: To show the **average price/rate of all past fixings** on a given leg of a deal.
    
- **Scope**: Only looks at **historic resets** (i.e., fixing dates that are already in the past).
    
- **Type**: **Day-weighted average** → weights each fixing by how many days it applies to, instead of just taking a simple arithmetic mean.
    

This result is useful for any **floating-price commodity trade** (swaps, forwards, futures, etc.) where a leg has **periodic resets** tied to an index.

---

### 🧮 Example

Suppose you have a **3-month swap leg** indexed to daily Brent prices, with monthly resets:

- **Jan reset (31 days)**: fixed at **$100**
    
- **Feb reset (28 days)**: fixed at **$95**
    
- **Mar reset (31 days)**: not fixed yet (future)
    

Now, if today is mid-March, only **Jan + Feb** are historic.

Day-weighted average =

(100×31)+(95×28)31+28\frac{(100 \times 31) + (95 \times 28)}{31 + 28}31+28(100×31)+(95×28)​ =3100+266059=576059≈97.63= \frac{3100 + 2660}{59} = \frac{5760}{59} ≈ 97.63=593100+2660​=595760​≈97.63

So the **Avg Hist By Leg Result = $97.63**

This will **update dynamically** as more resets occur.

---

### Why it matters in Endur

1. **For PnL Attribution**
    
    - Historic fixings are no longer valued off the curve; they are fixed.
        
    - This result tells you the effective historical average used for that leg’s settlement so far.
        
2. **For Pricing Validation**
    
    - Traders and middle office can compare average historical rate vs expected forward curve fixings.
        
3. **For Cashflow Estimation**
    
    - The final settlement will be based on both historical resets (fixed) + forward resets (still floating).
        
    - This result locks down the “fixed” part of the exposure.