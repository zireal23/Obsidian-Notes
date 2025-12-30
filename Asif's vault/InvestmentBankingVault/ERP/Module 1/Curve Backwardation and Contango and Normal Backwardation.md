# Spot, Forward, Contango, Backwardation, and Normal Backwardation

## 1. Curve Backwardation

**Definition:**

- Observed when **spot price today > forward price today**:
    

St>F(t,T)S_t > F(t,T)St​>F(t,T)

**Drivers:**

- Low inventories / tight supply
    
- Immediate demand spikes
    

**Interpretation:**

- Reflects **physical market tightness**
    
- Observable directly from market prices
    

**Example:**

- Spot gas today = $10
    
- Forward gas for month-end = $8
    

> Spot > Forward → curve backwardation

**Key Point:**

- Even when the spot is higher than the forward, one may **not buy the spot** if forward delivery is sufficient for needs, considering storage costs or location/quality constraints.
    

---

## 2. Contango (Curve)

**Definition:**

- Observed when **spot price today < forward price today**:
    

St<F(t,T)S_t < F(t,T)St​<F(t,T)

**Drivers:**

- High inventories / abundant supply
    
- Storage or carrying costs
    

**Interpretation:**

- Reflects **ample supply and cost-of-carry**
    
- Observable directly
    

**Example:**

- Spot gas today = $6
    
- Forward gas for month-end = $8
    

> Spot < Forward → curve contango

**Key Point:**

- Contango is purely about **today’s price vs forward**, independent of hedger incentives or risk premiums.
    

---

## 3. Normal Backwardation

**Definition (Keynes, Hicks):**

- Forward price **below the expected future spot price**:
    

F(t,T)<Et[ST]F(t,T) < \mathbb{E}_t[S_T]F(t,T)<Et​[ST​]

**Drivers:**

- Hedgers (producers) are **risk-averse**
    
- They sell forwards to **transfer price risk to speculators**
    
- Speculators require a **risk premium**
    

**Interpretation:**

- Not directly observable
    
- Explains why forward is systematically “cheap” relative to expected future spot
    

**Example:**

- Spot today = $6
    
- Forward = $8
    
- Expected future spot = $10
    

> Forward < Expected spot → normal backwardation

**Key Insight:**

- Even if the market is in **contango** (spot < forward), **normal backwardation can exist** if producers want to hedge risk and pay a premium to speculators:
    

St<F(t,T)<Et[ST]S_t < F(t,T) < \mathbb{E}_t[S_T]St​<F(t,T)<Et​[ST​]

- Spot cheap today → contango
    
- Forward below expected spot → producers paying risk premium → normal backwardation
    

---

## 4. Key Relationships

|Concept|Comparison|Observable?|Main Driver|
|---|---|---|---|
|Curve Backwardation|St>F(t,T)S_t > F(t,T)St​>F(t,T)|Yes|Physical tightness / low inventories|
|Contango|St<F(t,T)S_t < F(t,T)St​<F(t,T)|Yes|High inventories / storage costs|
|Normal Backwardation|F(t,T)<Et[ST]F(t,T) < \mathbb{E}_t[S_T]F(t,T)<Et​[ST​]|No|Hedger risk aversion / risk premium|

**Insights:**

1. Curve backwardation/contango = **snapshot of current market dynamics**
    
2. Normal backwardation = **theoretical risk premium due to hedger behavior**
    
3. They **can coexist** in the same market:
    

St<F(t,T)<Et[ST]S_t < F(t,T) < \mathbb{E}_t[S_T]St​<F(t,T)<Et​[ST​]

- Spot low → contango
    
- Forward below expected spot → normal backwardation
    
- Speculators profit if spot converges to expected future spot
    

---

## 5. Practical Takeaways

- **Curve shape** alone cannot indicate risk premium or expected spot movement.
    
- Always distinguish:
    
    - **Spot vs forward today** → market tightness (curve)
        
    - **Forward vs expected future spot** → risk transfer (normal backwardation)
        
- When analyzing futures or forwards for hedging/trading:
    
    - Check if market is contango/backwardation
        
    - Consider whether hedgers are paying risk premium (normal backwardation)
        
    - Recognize that **forward price may be between spot and expected future spot**, creating simultaneous contango + normal backwardation