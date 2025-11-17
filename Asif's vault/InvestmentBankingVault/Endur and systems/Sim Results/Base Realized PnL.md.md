## 1️⃣ Core definitions

|Result|Meaning|
|---|---|
|**MTM**|Present value of all current + future cash & physical flows (known + projected).|
|**Current Cash**|All cash flows **settling today**.|
|**Current Physical Equivalent**|Value of all **physical deliveries today** (price × volume).|
|**Unrealized PnL**|`MTM_today – MTM_yesterday + Yesterday.Current Cash + Yesterday.Current Phys Eqv`|
|**Realized PnL**|`Current Cash + Current Phys Eqv + Closeouts + Exercises`|
|**Base results**|Same as above, but **converted to the scenario’s base currency** using FX Result.|

---

## 2️⃣ Base formulas

- **Base MTM** = `MTM / FX_rate`
    
- **Base Current Cash** = `Current Cash / FX_rate`
    
- **Base Current Physical Eqv** = `Current Phys Eqv / FX_rate`
    
- **Base Unrealized PnL** =  
    `Base MTM_today – Base MTM_yesterday + Yesterday.Base Current Cash + Yesterday.Base Current Phys Eqv`
    
- **Base Realized PnL** =  
    `Base Current Cash + Base Current Phys Eqv + Closeout + Exercise effects`
    

> 🔹 Each day’s FX rate is used for that day’s conversions.  
> Do **not** convert both days at today’s FX.

---

## 3️⃣ Intuition

- **Unrealized PnL** tracks change in MTM that is _not yet realized_ in cash or physical flows.
    
- **Realized PnL** records what’s actually settled or closed out today.
    
- Over the life of a deal,  
    `Σ Unrealized PnL = Σ Realized PnL`.
    
- Base versions ensure all results are in a common currency for portfolio roll-up.
    

---

## 4️⃣ Worked example (CAD → USD base)

|Day|MTM (CAD)|FX (CAD/USD)|Base MTM (USD)|Curr Cash (CAD)|Base Curr Cash (USD)|
|---|---|---|---|---|---|
|2|1000|1.35|740.74|0|0|
|3|1100|1.40|785.71|0|0|
|4|1150|1.45|793.10|525|362.07|
|5|700|1.50|466.67|0|0|
|6|750|1.55|483.87|750|483.87|

### Base Unrealized PnL per day

`D2 = 740.74 – 0 + 0 + 0 = 740.74 D3 = 785.71 – 740.74 + 0 = 44.97 D4 = 793.10 – 785.71 + 0 = 7.39 D5 = 466.67 – 793.10 + 362.07 = 35.63 D6 = 483.87 – 466.67 + 0 = 17.20 Σ Base Unrealized ≈ 845.94 USD`

### Base Realized PnL per day

`D4 = 362.07 USD D6 = 483.87 USD Σ Base Realized = 845.94 USD`

✅ Totals match:  
`Σ Base Unrealized PnL = Σ Base Realized PnL`

---

## 5️⃣ Operational changes and alignment rules

1. **Alignment by leg number** – yesterday ↔ today matching is done strictly by leg index.  
    (Re-ordering or renumbering legs changes PnL mapping.)
    
2. **Currency/index changes** – yesterday’s values are converted into **today’s leg currency** before computing PnL.  
    Example:  
    `PNL = MTM_today – [spot(USD/CAD) × (MTM_yest – Cash_yest)]`
    
3. **Lost legs** – if legs were removed, their PnL is rolled into the **last surviving leg**.
    
    `Yesterday: 3 legs (100, –200, –100) Today: 2 legs (75, –100) → Leg 0 PNL = 75 – 100 = –25   Leg 1 PNL = –100 – (–200 – 100) = 350`
    
4. **Index assignment changes** – engine performs proper currency conversions before computing PnL.
    

---

## 6️⃣ Closeouts & Exercises

Currently, Realized PnL = Cash + Phys Eqv + (closeout + exercise effects).  
When these events start generating explicit cash flows (`Closeout Proceeds`, `Exercise Proceeds`),  
then → **Realized PnL ≡ Current Cash**.

---

## 7️⃣ Debug Checklist (when PnL looks off)

- ✅ Confirm MTM/FX snapshots used.
    
- ✅ Check FX orientation (Local/Base or Base/Local).
    
- ✅ Verify MTM includes current cash (depends on toolset).
    
- ✅ Confirm leg numbering & amendments.
    
- ✅ Watch for rounding/precision differences.
    
- ✅ Identify non-cash realized items (closeouts, exercises).
    
- ✅ Ensure correct definition of _“current day”_ (trade vs value date).
    

---

**Key takeaway:**

> Base Realized PnL = today’s settled economic reality,  
> while Base Unrealized PnL tracks how mark-to-market valuation changes between runs.  
> Over time, unrealized turns into realized as deals settle, always aligning in base currency.