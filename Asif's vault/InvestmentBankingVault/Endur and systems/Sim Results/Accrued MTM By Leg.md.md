# Accrued / MTM By Leg

**Category:** Endur Simulation Result  
**Result ID:** 205  
**Result Enum:** `ACCRUAL_MTM_BY_LEG_RESULT`  
**Result Class:** Leg Result  
**Toolsets:** Commodity

---

## Overview
Shows the **accrued value / mark-to-market (MtM)** broken down **per leg** of a trade.

- Useful for swaps, structured trades, or any multi-leg deal.  
- Provides visibility into the value contribution of each individual leg.

---

## Calculation
Derived from:
- `PV_TOTAL_BY_LEG_RESULT` (#126)  
- `FEE_PV_BY_LEG_RESULT` (#204)  

**Processing Steps**
1. **Accrued Flag**  
   - If the *Accrued MTM flag* on the deal = *Accrued*:  
     → Add `PV_TOTAL_BY_LEG` to the results.  

2. **Fees Flag**  
   - If a fee = *Accrued*:  
     → Add that discounted fee (`FEE_PV_BY_LEG`) to the leg’s total for the relevant period.  

\[
Accrued/MTM\ By\ Leg = \text{PV by Leg (if Accrued)} + \text{Accrued Fee PV by Leg}
\]

---

## Endur Context
- Reported at **leg level**, not whole-deal.  
- Allows detailed PnL attribution by leg.  
- Particularly important for **commodity swaps**, spreads, or trades with multiple pricing structures.

---

## Related
- [[PV Total By Leg (#126)]]  
- [[Fee PV By Leg (#204)]]  
- [[Accrued Forward Premium (#33)]]  
- [[Mark-to-Market (MtM)]]
