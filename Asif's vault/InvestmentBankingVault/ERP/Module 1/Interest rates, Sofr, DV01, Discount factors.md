# 📘 Interest Rates, SOFR, Discount Curves & DV01

_(A Deep Valuation & Risk Reference)_

---

## 1. Why interest rates matter in commodity trading at all

At first glance, commodities appear to be about:

- supply & demand
    
- weather
    
- logistics
    
- geopolitics
    

But **valuation** does not care _why_ a cashflow exists — only:

- **how much**
    
- **when**
    
- **with what certainty**
    

Any instrument with **future-dated cashflows** is exposed to **interest rates**.

Commodity swaps, therefore, are **not just commodity instruments**:

> They are **fixed-income instruments whose cashflows depend on prices**.

---

## 2. The foundational idea: time value of money

A dollar today is worth more than a dollar tomorrow because:

1. It can be invested
    
2. It can earn interest
    
3. It avoids funding costs
    
4. It avoids counterparty risk
    

Interest rates quantify **the cost of waiting**.

---

## 3. Discounting: the core valuation operation

All valuation engines reduce everything to:

![[Pasted image 20251229122622.png]]

Nothing more.  
Nothing less.

---

## 4. What exactly is a discount factor?

A **discount factor (DF)** answers:

> “How much is 1 unit of currency payable at time _t_ worth today?”

Properties:

- DF(today) = 1
    
- DF(future) < 1
    
- DF decreases as:
    
    - time increases
        
    - interest rates increase
        

---

## 5. From interest rates to discount factors

### Zero (spot) rates

Valuation uses **zero rates**, not deposit rates or coupon yields.

A **zero rate** is:

- the rate applicable to **one single cashflow**
    
- at **one specific maturity**
    

Each maturity has its own zero rate.

---

### Discount factor formula

![[Pasted image 20251229122641.png]]

Where:

- rtr_trt​ = zero rate for maturity ttt
    
- ttt = time in years
    

---

## 6. Simple discounting examples

Assume a zero rate of **5%**.

|Time (years)|DF|Meaning|
|---|---|---|
|0.0|1.000|Today|
|0.5|0.9759|$1 in 6 months ≈ 97.6¢|
|1.0|0.9524|$1 in 1 year ≈ 95.2¢|
|2.0|0.9070|$1 in 2 years ≈ 90.7¢|

---

## 7. SOFR: what it is and why it matters

### What SOFR represents

- Secured Overnight Financing Rate
    
- Based on **actual repo transactions**
    
- Reflects **near risk-free funding**
    
- Minimal credit risk
    

SOFR answers:

> “At what rate can I fund myself overnight with collateral?”

---

### Why SOFR is used for discounting

Discounting should reflect:

- **funding reality**
    
- **liquidity**
    
- **minimal credit risk**
    

Therefore:

- SOFR (or OIS) → discounting curve
    
- Credit & liquidity effects → handled separately (CVA/FVA)
    

---

## 8. Curve construction (conceptual, not procedural)

In practice:

1. Market instruments are observed  
    (OIS, futures, swaps, etc.)
    
2. These are **bootstrapped** into:
    
    - zero rates
        
3. Zero rates are converted into:
    
    - discount factors
        
4. Discount factors are used to:
    
    - value every cashflow
        

Valuation engines **never directly use quoted rates**.

---

## 9. Why discount curves matter more than interest rates

Interest rates:

- depend on compounding
    
- depend on day-count
    
- differ by convention
    

Discount factors:

- are pure numbers
    
- multiply cleanly
    
- are additive across cashflows
    

Internally:

> **All pricing engines think in discount factors.**

---

## 10. Valuing multiple cashflows (worked example)

### Cashflows

|Cashflow|Amount|Time (years)|
|---|---|---|
|CF1|10,000|0.5|
|CF2|10,000|1.0|
|CF3|10,000|2.0|

### SOFR zero curve

|Time|Zero rate|
|---|---|
|0.5|4.00%|
|1.0|4.20%|
|2.0|4.60%|

---

### Step 1: Compute discount factors

![[Pasted image 20251229122703.png]]

---

### Step 2: Compute present values

|CF|Amount|DF|PV|
|---|---|---|---|
|CF1|10,000|0.98058|9,805.8|
|CF2|10,000|0.95969|9,596.9|
|CF3|10,000|0.91376|9,137.6|

Total PV=28,540.3\text{Total PV} = 28,540.3Total PV=28,540.3

---

## 11. Where DV01 comes from (conceptual)

DV01 exists because:

- Discount factors depend on interest rates
    
- Interest rates move
    
- Therefore PV moves
    

DV01 measures **how much**.

---

## 12. DV01 definition (precise)

> **DV01 = change in PV for a +1 basis point parallel shift in rates**

1 bp = 0.01% = 0.0001

---

## 13. DV01 calculation: step-by-step

### Step 1: Bump the zero curve by +1 bp

|Time|Old|New|
|---|---|---|
|0.5|4.00%|4.01%|
|1.0|4.20%|4.21%|
|2.0|4.60%|4.61%|

---

### Step 2: Recompute discount factors

![[Pasted image 20251229122819.png]]

---

### Step 3: Recompute PV

|CF|Amount|New DF|New PV|
|---|---|---|---|
|CF1|10,000|0.98053|9,805.3|
|CF2|10,000|0.95960|9,596.0|
|CF3|10,000|0.91356|9,135.6|

![[Pasted image 20251229122837.png]]

---

### Step 4: Compute DV01

![[Pasted image 20251229122847.png]]

Interpretation:

- +1 bp increase in SOFR
    
- Portfolio loses USD 3.4 in value
    

---

## 14. DV01 intuition rules (extremely important)

### Rule 1: Time dominance

Longer-dated cashflows dominate DV01.

### Rule 2: Size dominance

Bigger cashflows → bigger DV01.

### Rule 3: Sign intuition

- Positive PV → negative DV01
    
- Negative PV → positive DV01
    

---

## 15. DV01 and commodity swaps

A commodity swap:

- Is a collection of future cashflows
    
- Each cashflow is discounted
    
- Therefore each contributes DV01
    

Fixing:

- Locks the **amount**
    
- Does NOT remove discounting
    
- DV01 remains until payment
    

---

## 16. Why futures don’t have DV01

Futures:

- Are marked to market **daily**
    
- Cash is exchanged daily
    
- No future unpaid cashflows
    

Therefore:

> No discounting → no DV01

---

## 17. How DV01 is used in practice

- Risk reports
    
- PnL explain
    
- Balance sheet sensitivity
    
- Interest rate hedging
    
- Stress testing
    

Often ignored by traders — never ignored by risk.

---

## 18. Ultimate synthesis (burn this in)

> Interest rates define discount factors  
> Discount factors define present value  
> Present value sensitivity defines DV01

Or more bluntly:

> **Every unpaid cashflow is a zero-coupon bond.**