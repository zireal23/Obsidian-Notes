# Accrued Forward Premium (Endur)

**Category:** Endur Simulation Result  
**Result ID:** 33  
**Result Enum:** `ACCRUED_FWD_PREMIUM_RESULT`  
**Result Class:** Transaction Result (Tran Result)  
**Toolsets:** `ComFut`, `ComFwd`

---

## Overview
Accrued Forward Premium represents the **pro-rated recognition of the forward premium** on a deal from its start date until settlement.

- Formula:  
  \[
  (Trade\ Price - Spot\ Price\ at\ Trade\ Date) \times Notional
  \]  
- Accrued **daily** from start date → settlement date.  
- Uses **spot on trade date**, not daily changing spot.  
- Only posts after the default start date.  

---

## Example Deal
- Notional = 1,000 barrels  
- Trade Price = $55  
- Spot (trade date) = $50  
- Settlement = 30 days later  

**Forward Premium** = (55 – 50) × 1000 = **$5,000**  
**Daily Accrual** = 5000 ÷ 30 = **166.67/day**

Timeline:  
| Day | Daily Accrual | Cumulative |
|-----|---------------|------------|
| 1   | 166.67        | 166.67     |
| 15  | 166.67        | 2,500.05   |
| 30  | 166.67        | 5,000.00   |

---

## Why only trade-date spot?
- Forward premium is **locked at inception** → it never changes.  
- Daily spot/forward moves are captured by **Mark-to-Market (MtM)**, not by accrued premium.  

---

## Why accrue daily if it doesn’t change?
1. **Smooth PnL recognition** instead of one big jump on settlement day.  
2. **Accounting compliance** (IFRS/GAAP) requires amortisation of premiums/fees.  
3. **Endur PnL attribution**: separates carry vs. market-driven PnL.  
4. **Risk analysis**: shows how much is earned just by holding (carry) vs. market movement.  

---

## Full Lifecycle PnL Example

| Day | Forward Curve (1m) | MtM ( (Fwd–55)×1000 ) | Accrued Premium (cum.) | Final Realised Impact |
|-----|---------------------|------------------------|-------------------------|-----------------------|
| 1   | 56                  | +1,000                 | +166.67                 | —                     |
| 15  | 53                  | –2,000                 | +2,500                  | —                     |
| 30  | 58 (settle)         | +3,000                 | +5,000                  | Realised = –3,000     |

---

## Key Takeaways
- **Accrued Premium** = fixed carry (time-based recognition of inception premium).  
- **MtM** = fluctuates daily with market moves.  
- **At settlement**: accrued + MtM collapse into **realised PnL** = (Trade Price – Final Fixing) × Notional.  

---

## Related
- [[Mark-to-Market (MtM)]]
- [[Forward Price]]
- [[Spot Price]]
- [[Premium / Discount in Forwards]]
- [[PnL Attribution in Endur]]
