## 📘 Oil Futures Pricing

### 🧠 Summary

The pricing of oil futures is primarily explained using two theoretical frameworks:

1. **Theory of Storage** (Cost-of-Carry Model)
    
2. **Risk Premium Hypothesis** (Unbiased Expectations)
    

Both models describe how **spot** and **futures prices** relate to each other, and provide a foundation for explaining the **term structure** of oil futures.

---

## 🧱 Assumptions in Futures Pricing

> These assumptions apply to both the Theory of Storage and Risk Premium models:

1. **No Arbitrage**: Markets don't allow persistent arbitrage opportunities.
    
2. **No Transaction Costs**: Traders don't incur costs during trading.
    
3. **Same Taxation**: All participants face the same tax rate.
    
4. **Same Interest Rates**: All participants can borrow/lend at the same risk-free rate.
    

---

## 📦 1. Theory of Storage Hypothesis

**Originators**: Kaldor (1939), Working (1949, 1984), Brennan (1958)

This theory considers:

- Storage
    
- Deterioration of commodities
    
- Supply fluctuations
    
- Consumption
    
- Benefits from physical ownership (→ **convenience yield**)
    

---

### 🧮 Key Concepts

|Term|Meaning|
|---|---|
|`S`|Spot price|
|`F`|Futures price|
|`r`|Risk-free interest rate|
|`τ`|Time to maturity `(T - t)`|
|`U`|Storage cost (present value)|
|`CY`|Convenience yield|
|`CC`|Cost of Carry (marginal storage costs)|

---

### 🔢 Pricing Formulas

#### 1. Basic Financial Asset Futures:

ini

CopyEdit

`F = S * e^(r * τ)`

(No income, no storage costs)

#### 2. With Storage Costs:

ini

CopyEdit

`F = (S + U) * e^(r * τ)`

#### 3. With Convenience Yield:

$$

`F * e^(CY * τ) = (S + U) * e^(r * τ)`
$$
$$
`F = S * e^[(r + CC - CY) * τ]`
$$

---

### 📊 Diagram: Theory of Storage Pricing Model

---

### 🔍 Interpretation

- **Convenience Yield (CY)** is a non-monetary benefit from physically holding the asset (like avoiding shortages).
    
- If futures prices are too low, arbitrageurs can:
    
    1. Sell the commodity in spot market
        
    2. Buy futures contract
        
    3. Avoid storage costs
        

---

## 📈 2. Risk Premium Hypothesis

**Originator**: Keynes (1930), "Theory of Normal Backwardation"

### 📝 Concept

- Futures prices embed investor expectations **plus** a **risk premium**.
    
- The **risk premium** compensates for price uncertainty at maturity.
    

> A trader buying a futures contract faces the risk that the actual spot price at maturity may be lower than the contract price.

---

### 🔢 Risk Premium Formula

ini

CopyEdit

`F = E[S(T)] * e^(-rp * τ)`

Where:

- `E[S(T)]` = Expected spot price at maturity
    
- `rp` = Risk premium (continuously compounded)
    

---

### 🔁 Relationship to Theory of Storage

These two theories can be reconciled:

> **Convenience Yield = Expected deviation in spot price not explained by risk-free rate and risk premium.**

---

## 🧭 Insights

- **Backwardation** (F < S) can be due to:
    
    - High convenience yield
        
    - High risk premium (short hedgers dominate)
        
- **Contango** (F > S) can result from:
    
    - High storage costs
        
    - Low or negative convenience yield

![[Pasted image 20250520115543.png]]
        

---

## 🧠 Key Takeaways

- The Theory of Storage focuses on **physical market constraints and benefits** (inventory holding).
    
- The Risk Premium model sees futures prices as reflecting **market expectations** and **risk preferences**.
    
- Both models are essential to fully understand **oil futures pricing** and are **not mutually exclusive**.
    

---

## 📚 Further Reading

- Kaldor (1939) – Speculation and Economic Stability
    
- Keynes (1930) – A Treatise on Money
    
- Brennan (1958) – The Supply of Storage
    
- Working (1949, 1984) – The Theory of Price of Storage
