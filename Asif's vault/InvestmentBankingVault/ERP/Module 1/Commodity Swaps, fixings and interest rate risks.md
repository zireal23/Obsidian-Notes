## 1. What a commodity swap is (structural view)

A **commodity swap** is a **financial contract** where two counterparties exchange:

- a **fixed price**
    
- for a **floating market price**
    

on:

- the **same commodity**
    
- the **same notional volume**
    
- across **multiple settlement periods**
    
- **without physical delivery**
    

The purpose is **price risk transfer**, not commodity movement.

---

## 2. Core components of a swap

Every commodity swap must define:

1. **Underlying commodity**
    
2. **Notional volume** (per period)
    
3. **Fixed price**
    
4. **Floating price benchmark** (index)
    
5. **Settlement periods**
    
6. **Fixing dates**
    
7. **Payment (cashflow) dates**
    

Each settlement period behaves like a **mini-instrument** inside the swap.

---

## 3. Period structure (most important mental model)

Each swap period has **four economically distinct dates**:

|Stage|Meaning|
|---|---|
|Trade date|Swap is agreed|
|Valuation dates|Daily MTM changes|
|Fixing date|Floating price becomes known|
|Payment date|Cash is exchanged|

**Fixing and payment are NOT the same thing.**

---

## 4. Fixed vs floating leg mechanics

### Fixed leg

- Fixed price × volume
    
- Known from trade inception
    
- Discounted until payment
    

### Floating leg

- Unknown until fixing
    
- Projected using **forward curve**
    
- After fixing → amount becomes known
    
- Discounted until payment
    

---

## 5. Pricing principle (why swaps start at zero value)

At inception:

> **PV(Fixed leg) = PV(Floating leg)**

Otherwise, one counterparty would be giving value away.

This determines the **fixed swap price**.

---

## 6. Valuation logic (how MTM is computed)

At any valuation date:

MTM=∑(PV of floating cashflows)−∑(PV of fixed cashflows)\text{MTM} = \sum (\text{PV of floating cashflows}) - \sum (\text{PV of fixed cashflows})MTM=∑(PV of floating cashflows)−∑(PV of fixed cashflows)

Cashflows fall into three states:

|State|Valuation source|
|---|---|
|Unfixed|Forward curve|
|Fixed but unpaid|Known amount, discounted|
|Settled|Zero value|

---

## 7. Sample swap used in walkthrough

**Trade details**

- Commodity: Natural Gas
    
- Volume: 10,000 MMBtu / month
    
- Tenor: 3 months
    
- Fixed price: 4.00 USD/MMBtu
    
- You: Pay fixed, receive floating
    

**Forward curve at valuation**

|Month|Forward|
|---|---|
|Jan|4.10|
|Feb|4.20|
|Mar|4.30|

**Discount curve (SOFR zero rates)**

|Time (years)|Rate|
|---|---|
|0.25|4.0%|
|0.50|4.1%|
|0.75|4.2%|

---

## 8. Valuation before fixing (T₀)

- Fixed leg PV = 117,592
    
- Floating leg PV = 123,452
    

MTM=+5,860\text{MTM} = +5,860MTM=+5,860

Interpretation:

- Swap is **in-the-money**
    
- This is **unrealized PnL**
    

---

## 9. Fixing event (January)

- January index fixes at **4.15**
    
- January floating cashflow becomes known
    
- Forward curve no longer used for January
    

**Net January cashflow**

(4.15−4.00)×10,000=+1,500(4.15 - 4.00) \times 10,000 = +1,500(4.15−4.00)×10,000=+1,500

This amount is **still discounted** until payment.

---

## 10. Settlement

- Cash is exchanged
    
- That period’s PV becomes **zero**
    
- Unrealized PnL converts to realized PnL
    

---

## 11. Risk evolution summary

|Phase|Risks present|
|---|---|
|Before fixing|Price + rate + time|
|After fixing|Rate + time|
|After payment|None|

---

## 12. Master mental model

> A commodity swap is a **portfolio of zero-coupon bonds**  
> Fixing locks the **amount**  
> Payment kills the **value**