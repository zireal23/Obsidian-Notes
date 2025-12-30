# When Futures Curves Are Dangerous Proxies for Physical Forwards

## Core idea (one sentence)

> **Futures curves are safe proxies only when financial and physical markets are tightly coupled; they become dangerous when physical optionality, constraints, or credit realities dominate price formation.**

Let’s break _exactly_ when and why that coupling breaks.

---

## 1. Location Mismatch & Basis Volatility

### What the model assumes

- Futures = “representative price”
    
- Basis = stable or mean-reverting add-on
    

### When this breaks

- Congestion
    
- Pipeline outages
    
- LNG terminal constraints
    
- Regional demand spikes (heat waves, cold snaps)
    

### Example (Natural Gas)

- Henry Hub futures used as proxy for:
    
    - Waha
        
    - AECO
        
    - TTF-linked LNG feedgas
        
- During constraints:
    
    - Basis explodes
        
    - Forward physical prices **disconnect completely**
        

📌 **Danger signal**:  
If the _basis curve itself_ is volatile, convex, or regime-switching, futures are a **bad anchor**.

---

## 2. Delivery Optionality Embedded in Futures

### Hidden futures option

Most energy futures embed **short optionality**:

- Delivery timing flexibility
    
- Delivery location baskets
    
- Quality tolerances
    
- Alternative Delivery Procedures (ADPs)
    

### Why this matters

- Futures price = **worst-case deliverable economics**
    
- Physical forward = **specific asset economics**
    

### Example

- Crude futures allow delivery from multiple grades/locations
    
- Cheapest-to-deliver dominates futures price
    
- Your physical contract may **not have access** to that CTD barrel
    

📌 **Result**: Futures price is **systematically lower** than asset-specific forwards in stressed markets.

---

## 3. Storage Constraints & Inventory Regimes

### Textbook assumption

- Storage arbitrage links spot ↔ forwards ↔ futures
    

### Reality

Storage is:

- Finite
    
- Unevenly distributed
    
- Often fully booked
    

### Breakdown scenario

- Storage near delivery point is full
    
- Spot collapses
    
- Futures still reflect deferred expectations
    

### Example (Gas or Power)

- Negative spot prices
    
- Forward physical still positive due to:
    
    - Firm transport
        
    - Embedded load obligations
        

📌 **Danger signal**:  
If **storage constraints bind**, futures curves lose their arbitrage anchor.

---

## 4. Credit & Liquidity Segmentation

### Futures world

- Daily margining
    
- High liquidity
    
- No credit thresholds
    

### Physical OTC world

- Bilateral credit limits
    
- Thresholds
    
- Liquidity varies by tenor/location
    

### Consequence

- Physical forwards may trade at a **credit premium**
    
- Futures curves **ignore this premium**
    

### This matters especially for:

- Long-dated forwards
    
- Small producers
    
- Emerging market counterparties
    

📌 **Danger signal**:  
If your counterparty credit materially affects pricing, futures are **underpricing reality**.

---

## 5. Regulatory & Tax Distortions

### Futures are:

- Financial instruments
    
- Regulated at exchange level
    

### Physical forwards are:

- Subject to:
    
    - Fuel taxes
        
    - Carbon costs
        
    - Environmental obligations
        
    - Local market rules
        

### Example

- Power forwards embedding:
    
    - Capacity payments
        
    - Renewable obligations
        
- Futures reflect none of these
    

📌 **Result**: Futures curve misses **structural cost components**.

---

## 6. Index Construction Lag & Feedback Loops

### Energy forwards often price as:

> Index + basis

Where the index itself is:

- Based on **historical bidweek trades**
    
- Thinly traded
    
- Subject to reporting delays
    

### Failure mode

- Futures move rapidly
    
- Index lags
    
- Physical forwards temporarily decouple
    

📌 **Especially dangerous** in:

- Fast-moving markets
    
- Weather-driven demand shocks
    

---

## 7. Interest Rate & Inflation Regime Shifts

### Normally ignored

- Futures ≈ forwards
    

### Becomes dangerous when:

- High inflation
    
- Rising rates
    
- Commodity prices drive rates (not vice versa)
    

### Effect

- Mark-to-market economics dominate
    
- Futures incorporate reinvestment optionality
    
- Physical forwards do not
    

📌 **Rare but regime-critical risk**.

---

## 8. Seasonality & Shape Risk

### Futures curves

- Often smoother
    
- Exchange liquidity concentrates in front months
    

### Physical reality

- Extreme intra-season spikes
    
- Shoulder months behave nonlinearly
    

### Example

- Gas winter strips vs individual Jan/Feb forwards
    
- Power summer peaks vs average contracts
    

📌 **Averages hide convexity** → futures understate risk.

---

# Summary Table

|Condition|Futures as Proxy?|Why|
|---|---|---|
|Stable basis|✅ Safe|Strong financial–physical linkage|
|Congestion / outages|❌ Dangerous|Basis dominates|
|CTD optionality|❌ Dangerous|Futures price ≠ asset price|
|Full storage|❌ Dangerous|Arbitrage broken|
|Credit-sensitive deals|❌ Dangerous|Futures ignore credit|
|Regulatory overlays|❌ Dangerous|Structural costs omitted|
|Fast regime shifts|❌ Dangerous|Indices lag|
|Calm macro, low rates|✅ Usually safe|Historical norm|

---

## How Good Traders & Risk Teams Handle This

- Futures curves = **starting point, not truth**
    
- Build:
    
    - Independent **basis curves**
        
    - Location-specific **forward curves**
        
    - Stress scenarios on basis, not flat price
        
- Treat futures as:
    
    > _Liquidity instruments_, not _price discovery instruments_, during stress