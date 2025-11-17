# Amendment MTM Detail

**Category:** Endur Simulation Result  
**Result ID:** 223  
**Result Enum:** `AMENDED_MTM_DETAIL_RESULT`  
**Result Class:** General Result  
**Toolsets:** All toolsets  
**Reval Type:** EOD only

---

## Overview
Shows the **Amendment MTM Detail** for deals that were amended on the reval date.

- Drilldown result designed to **explain PnL from deal amendments**.  
- Provides visibility into the **old version (Amended)** and the **new version (Validated)** of a deal.  
- The difference in PV between the two versions = **Amendment PnL**.  

---

## Columns Returned
- **deal_num** – Deal identifier  
- **tran_num** – Transaction identifier  
- **deal_leg, deal_pdc** – Leg and period info  
- **tran_status** – Amended / Validated  
- **event_source, ins_seq_num** – Instrument details  
- **payment_date** – Cashflow/payment date  
- **pv** – Present Value (discounted)  
- **proceeds, security_value** (v6.0+)  
- **currency**  

---

## How It Works
1. If a deal is **amended**:  
   - The *Amended* version’s PV is shown as **negative**.  
2. The new *Validated* version’s PV is included as normal.  
3. Netting the two = **Amendment impact on PnL**.  

---

## Example
- Deal Num: 1234  
- **Amended Version**: Tran 1234, PV = 84.50 → shown as (84.50)  
- **Validated Version**: Tran 8999, PV = 90.00  

Result:  

| deal_num | tran_num | tran_status | PV      |
|----------|----------|-------------|---------|
| 1234     | 1234     | Amended     | (84.50) |
| 1234     | 8999     | Validated   | 90.00   |

**Net Impact**  
= –84.50 + 90.00  
= **+5.50 (Amendment PnL)**

---

## Use Cases
- Isolate PnL due to trade changes vs. market moves.  
- Provides audit trail for amended deals.  
- Required for **accurate PnL attribution reports**.  

---

## Related
- [[Mark-to-Market (MtM)]]  
- [[PnL Attribution in Endur]]  
- [[Accrued Forward Premium (#33)]]  
- [[Accrued / MTM By Leg (#205)]]
