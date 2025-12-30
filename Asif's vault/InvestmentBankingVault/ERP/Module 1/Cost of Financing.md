# 📘 Cost of Financing (Funding Cost)

### Economic Meaning, Valuation Link, PnL Mechanics, and Institutional Reality

---

## 1. What “Cost of Financing” really is (strip the jargon)

**Cost of Financing (CoF)** answers one brutally simple question:

> **What does it cost (or earn) to carry a position over time because cash is not exchanged immediately?**

It exists because:

- valuation happens **today**
    
- cash moves **later**
    
- someone must bridge the gap
    

That bridge has a cost (or benefit).

---

## 2. The foundational distinction (this is critical)

Many people confuse these concepts:

|Concept|Purpose|Static / Dynamic|
|---|---|---|
|**Discounting**|Value future cashflows today|Static|
|**Cost of financing**|Explain PnL drift as time passes|Dynamic|

> Discounting answers **“What is it worth?”**  
> Financing answers **“What does it earn or cost while I wait?”**

They are related — but **not interchangeable**.

---

## 3. Why cost of financing exists in swaps (core intuition)

Commodity swaps:

- exchange **no cash upfront**
    
- generate **future net cashflows**
    
- have **unrealized MTM** for long periods
    

That unrealized MTM:

- is an asset (if positive)
    
- or a liability (if negative)
    

Assets must be funded.  
Liabilities free up funding.

---

## 4. The clean mental model (burn this in)

> **Every unpaid MTM behaves like a loan.**

- Positive MTM → you are _lending_ money to the future → you earn financing
    
- Negative MTM → you are _borrowing_ money from the future → you pay financing
    

This is true regardless of product.

---

## 5. Financing vs price vs rate PnL (PnL explain framework)

Daily PnL is usually decomposed as:

PnL=Price PnL+Rate PnL+Time (Theta)+Financing PnL\text{PnL} = \text{Price PnL} + \text{Rate PnL} + \text{Time (Theta)} + \text{Financing PnL}PnL=Price PnL+Rate PnL+Time (Theta)+Financing PnL

Where:

|Component|Source|
|---|---|
|Price PnL|Commodity forward/index movement|
|Rate PnL|Interest rate curve movement (DV01)|
|Time / Theta|Cashflows getting closer|
|Financing PnL|Cost/benefit of funding MTM|

Some desks combine **time + financing** — but conceptually they are different.

---

## 6. The financing rate: what rate is actually used?

There is **no single “correct” financing rate**. It depends on perspective.

Common choices:

|Perspective|Rate Used|
|---|---|
|Treasury|Internal funding curve|
|Risk|OIS / SOFR|
|Finance|Policy-defined funding rate|
|XVA|Funding curve vs discount curve|
|Desk-level|Simplified SOFR + spread|

Key principle:

> **Financing rate reflects how the firm actually funds money, not market convenience.**

---

## 7. Simple financing PnL formula (desk approximation)

For small time steps:

Financing PnL≈Yesterday MTM×r×Δt\text{Financing PnL} \approx \text{Yesterday MTM} \times r \times \Delta tFinancing PnL≈Yesterday MTM×r×Δt

Where:

- MTM = previous day’s mark
    
- rrr = financing rate
    
- Δt\Delta tΔt = time fraction (e.g. 1/252)
    

---

## 8. Worked example: financing PnL on a swap

### Setup

- Swap MTM today: **+5,860**
    
- Financing rate: **4.5%**
    
- One trading day: **1 / 252**
    

### Financing PnL

5,860×0.045×1252≈+1.055{,}860 \times 0.045 \times \frac{1}{252} \approx \boxed{+1.05}5,860×0.045×2521​≈+1.05​

Interpretation:

- No price movement
    
- No rate movement
    
- Still earned **$1.05** by holding the position
    

That is **pure financing carry**.

---

## 9. Financing vs DV01 (very important distinction)

|Aspect|Financing|DV01|
|---|---|---|
|Trigger|Passage of time|Rate movement|
|Depends on|MTM level|PV sensitivity|
|Predictability|Deterministic|Market-driven|
|Hedged by|Funding policy|IR instruments|

People often confuse **rate PnL** with **financing PnL** — they are different.

---

## 10. Financing and fixing (subtle but crucial)

### Before fixing

- MTM fluctuates with price
    
- Financing accrues daily
    

### After fixing (before payment)

- Amount is known
    
- MTM still exists
    
- Financing **continues**
    

### After payment

- MTM = 0
    
- Financing stops
    

> **Fixing removes price risk, not financing risk.**

---

## 11. Financing and settlement timing

The longer the gap between:

- fixing date
    
- payment date
    

the larger:

- financing impact
    
- liquidity exposure
    

This is why:

- settlement calendars matter
    
- operational delays have real PnL impact
    

---

## 12. Financing vs discount curve mismatch (gateway to FVA)

If:

- discount curve ≠ funding curve
    

then:

- systematic carry PnL appears
    
- even in a “perfectly hedged” book
    

This difference is the **economic root of Funding Valuation Adjustment (FVA)**.

Many desks:

- ignore it explicitly
    
- absorb it implicitly via financing PnL
    

---

## 13. How financing is treated across teams

### Trading

- Calls it “carry”
    
- Often underestimates its importance
    

### Risk

- Cares only if it accumulates materially
    

### Treasury

- Owns the funding curve
    
- Cares deeply
    

### Finance

- Tracks financing PnL explicitly
    
- Reconciles it to balance sheet
    

### XVA

- Models it explicitly (FVA)
    

Understanding all five views is rare — and powerful.

---

## 14. Cost of financing vs margining

Margining reduces:

- credit exposure
    

But:

- does **not eliminate financing**
    

Why?

- collateral itself must be funded
    
- margin cash has opportunity cost
    

So:

> Collateralization changes _who_ funds, not _whether_ funding exists.

---

## 15. Financing in ETRM systems (implementation view)

Typical system flow:

1. Yesterday’s MTM snapshot
    
2. Apply financing rate
    
3. Accrue carry PnL
    
4. Attribute to desk / book
    
5. Roll forward daily
    

This is **accrual**, not repricing.

---

## 16. Why traders often ignore financing (and why that’s dangerous)

Reasons traders ignore it:

- Small day-to-day
    
- Not driven by skill
    
- Feels “finance-owned”
    

Why this fails:

- Large books
    
- High-rate environments
    
- Long-dated swaps
    

→ Financing becomes **material PnL**

---

## 17. Unified mental model (ties everything together)

> Each unpaid cashflow is a bond  
> Discounting prices the bond  
> DV01 measures rate sensitivity  
> Financing measures carry  
> Settlement kills the bond

This model works across:

- commodities
    
- FX
    
- rates
    
- credit