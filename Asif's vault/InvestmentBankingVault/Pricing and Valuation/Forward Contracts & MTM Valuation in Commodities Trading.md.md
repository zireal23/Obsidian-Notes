# 🛢️ Forward Contracts & MTM Valuation in Commodities Trading (Endur Context)

## 📘 Overview

This note covers:
- The lifecycle of a forward contract
- Key definitions: deal, transaction, instrument
- Why mark-to-market (MTM) is calculated for forwards
- A detailed MTM example with Endur integration
- Concepts of basis pricing and index-linked deals

---

## 🔁 Forward Contract Lifecycle

1. **Deal Capture**
   - Trader or marketer enters the deal into a trading system (e.g., Endur).
   - Includes quantity, price formula, location, counterparty, delivery dates.

2. **Deal Booking**
   - Booking into front-office systems.
   - Integration with risk, operations, and settlement teams.

3. **Risk & P&L Monitoring**
   - MTM values calculated daily using updated forward curves.
   - P&L and exposure monitored continuously.

4. **Scheduling & Nominations**
   - Ops teams handle physical delivery scheduling (e.g., to pipeline).

5. **Settlement**
   - Invoicing and actual payment after delivery.
   - Based on final index values + agreed differential.

---

## 🔑 Key Terms in Endur

| Term         | Meaning in Endur                            |
|--------------|---------------------------------------------|
| **Deal**     | The commercial agreement captured in the system |
| **Transaction** | A lifecycle event tied to a deal (e.g., amendment, settlement) |
| **Instrument** | The product template defining how the deal behaves (e.g., Physical Gas Forward) |

---

## 📐 Basis Pricing (Price Differential)

- **Index-Based Deal:** Priced at `Index + Basis`
- **Basis (a.k.a. Differential):** Trader-defined price uplift/downlift reflecting:
  - Regional differences (e.g., Henry Hub vs. Transco Z6)
  - Transport costs
  - Liquidity
  - Trader’s margin

> Example: "Sell at Henry Hub + $0.85/MMBtu"

---

## 🧾 Example Deal

| Attribute        | Value                         |
|------------------|-------------------------------|
| Commodity        | Natural Gas                   |
| Quantity         | 30,000 MMBtu/day              |
| Delivery Period  | June 1–30, 2025               |
| Location         | Transco Zone 6 NY             |
| Pricing          | NYMEX Henry Hub Index + $0.85 |
| Deal Price (on May 1) | $3.60/MMBtu (2.75 + 0.85)  |

---

## 📊 Mark-to-Market (MTM) Valuation for Forwards

### 🤔 Why MTM a Forward Deal?
- Track **unrealized P&L**
- Monitor **credit risk / exposure**
- Aid in **risk management**
- Fulfill **accounting** or **regulatory** needs

> Unlike futures, there's **no daily margining**, but MTM still shows what the trade is worth "if liquidated today."

---

## 📉 MTM Example Calculation

### 📅 On Trade Date (May 1):
- Forward curve for June: **$2.75/MMBtu**
- Deal Price: `$2.75 + 0.85 = $3.60/MMBtu`

**Contract Value:**
30,000 × 30 days × $3.60 = $3.24 million

---

### 📅 On MTM Date (May 15):
- Forward curve has dropped to **$2.35/MMBtu**
- MTM price: `$2.35 + 0.85 = $3.20/MMBtu`

**MTM Difference:**
Price difference: $3.60 - $3.20 = $0.40/MMBtu MTM = 30,000 × 30 × $0.40 = $360,000 unrealized gain

---

## 🛠 How This Appears in Endur

| Module              | Info Tracked                        |
|---------------------|-------------------------------------|
| Deal Viewer         | Deal details (volume, formula)      |
| Curve Viewer        | Forward curve for June              |
| Valuation Engine    | MTM and P&L                         |
| Risk Viewer         | Volume exposure and VAR             |
| Accounting Reports  | Unrealized P&L and fair value       |

---

## ✅ Summary

- **Basis = price differential** applied by trader on top of index
- **MTM** is crucial for risk and P&L tracking — even for non-exchange traded forwards
- **Endur** calculates MTM daily using pricing curves, not for margining but for valuation
- Traders want to know if they’re in or out of the money, even before settlement

---

## 🧠 Resources to Learn More

- [CME Group – Natural Gas Futures & Basis Pricing](https://www.cmegroup.com/markets/energy/natural-gas.html)
- [Investopedia – Mark-to-Market](https://www.investopedia.com/terms/m/marktomarket.asp)
- [Allegro/Endur user guides (if you have access)]
- [“Energy Trading and Risk Management” – Iris Marie Mack]

---