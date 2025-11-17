## 📘 Volatility in Endur

### 🧠 Concept Overview

Volatility represents the **uncertainty or variability** in future price movements of an underlying commodity, FX rate, or interest rate.  
In Endur, it is a **market data input** used for pricing options, valuing optionality in structured deals, and simulating risk metrics (PnL, VaR, Greeks).

---

### ⚙️ Role of Volatility in Endur

Volatility is used in two main contexts:

1. **Market Data Layer**
    
    - Defined as _volatility curves or surfaces_.
        
    - Stored in the **Volatility Definition** table.
        
    - Loaded from market feeds or entered manually.
        
2. **Valuation & Simulation Layer**
    
    - Used by pricing models (Black, Bachelier, Hull-White, etc.).
        
    - Inputs into:
        
        - Option pricing
            
        - Greeks (Vega, Delta, Gamma)
            
        - VaR simulations
            
        - PnL Explain
            

---

### 🧱 Volatility Structure

Volatility is modeled as a **multi-dimensional surface**, typically 2D (sometimes 3D), showing how volatility varies with strike and expiry.

|Dimension|Represents|Captures|
|---|---|---|
|**Moneyness (Strike)**|Relative strike level vs forward|Smile / Skew|
|**Expiration (Tenor)**|Time to option expiry|Term structure of volatility|

---

### 📊 Moneyness Explained

**Moneyness** measures how far the strike is from the current forward price.

|Type|Definition (for a call)|Example (Underlying = 100)|
|---|---|---|
|In-the-money (ITM)|Strike < Forward|90|
|At-the-money (ATM)|Strike ≈ Forward|100|
|Out-of-the-money (OTM)|Strike > Forward|110|

Volatility behaves differently across moneyness levels, creating patterns such as:

- **Volatility skew** (equities, FX): vol decreases with higher strike.
    
- **Inverse skew** (commodities): vol increases for OTM calls due to supply risks.
    

Endur models this dependence on the **X-axis (Moneyness)**.

---

### ⏱️ Expiration Explained

The **Y-axis (Expiration)** captures how volatility changes over time:

- **Short-term options:** higher vol due to immediate market events.
    
- **Long-term options:** lower vol as uncertainty averages out.
    

This forms the **term structure of volatility**, which can be:

- **Contango:** rising vol with maturity.
    
- **Backwardation:** falling vol with maturity.
    

---

### 📈 The Volatility Surface

3D representation of volatility behavior:

             `Volatility (%) ^                   |       0.6 ┤                  •           |                •           |             •           |          •           |       •           |    •           | •           |_________________________>            Moneyness (Strike/Fwd)     Expiration (Tenor)`

- **X-axis:** Strike / Moneyness
    
- **Y-axis:** Expiration
    
- **Z-axis:** Volatility
    

---

### 🧮 Example Volatility Matrix (Endur Representation)

|Expiry|80% Moneyness|100% Moneyness|120% Moneyness|
|---|---|---|---|
|1M|45%|40%|42%|
|3M|43%|38%|40%|
|6M|41%|36%|38%|
|1Y|39%|35%|37%|

Defined in the **Volatility Definition** window:

- Dimensions → Expiry, Moneyness
    
- Grid Points → specific expiry and strike values
    
- Interpolation → method to estimate vol between grid points
    

---

### 🧩 Why “Moneyness” Instead of Absolute Strike?

- Forward prices differ by expiry → absolute strikes distort patterns.
    
- Moneyness normalizes the surface relative to the forward price.
    
- Makes the surface **stable and comparable across tenors**.
    

Endur often defines the strike axis as **Strike (% of Forward)**, e.g.:

- 90% → 0.9 × forward
    
- 100% → at-the-money
    
- 110% → 1.1 × forward
    

---

### 🔧 Calibration and Interpolation

Market quotes exist for a few standard strikes/expiries (e.g., ATM, 25Δ, 10Δ).  
Endur interpolates between them to create a continuous surface:

- Between expiries → **term interpolation**
    
- Between strikes → **smile interpolation**
    

This allows Endur to find volatility for _any_ option expiry and strike.

---

### 💼 Uses of Volatility in Endur

|Area|Usage|
|---|---|
|**Option Pricing**|Inputs to pricing models for fair value|
|**VaR / Simulations**|Drives simulated price paths|
|**Sensitivities**|Vega, Volga, Vomma calculations|
|**PNL Explain**|Identifies PnL from vol changes|
|**Scenario Analysis**|Tests volatility shift impacts|

---

### 🧾 Summary

| Concept                    | Description                                                              |
| -------------------------- | ------------------------------------------------------------------------ |
| **Volatility Surface**     | 2D grid of vol values vs moneyness & expiry                              |
| **Purpose**                | Reflects market-implied uncertainty across time & strike                 |
| **Moneyness Axis**         | Captures skew/smile (strike dependence)                                  |
| **Expiry Axis**            | Captures term structure (time dependence)                                |
| **Endur Representation**   | Defined in Volatility Definition → matrix form                           |
| **Effective Input (#169)** | Final combined volatilities used in pricing/simulation after adjustments |