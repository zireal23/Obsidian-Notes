## 📚 Commodities + Endur Structured Learning Plan

---

## **Tags**: `#learning-plan` `#commodities` `#endur`  
**Created**: {{date}}

### 🎯 Goal

To develop a **deep, structured understanding** of commodities trading (physical & financial) and how it is represented, simulated, and processed inside **Openlink Endur**, by layering conceptual knowledge with technical mapping.

---

## 🧱 Layered Learning Framework

> Use this structure to link every concept across **three levels** for maximum retention.

| Layer       | Focus                                    | Example                                                      |
| ----------- | ---------------------------------------- | ------------------------------------------------------------ |
| **Level 1** | Core Commodities Concepts                | e.g., Forward contracts, swaps, VaR                          |
| **Level 2** | Endur Representation (ETRM layer)        | Deal types, simulations, reporting, tables                   |
| **Level 3** | Real-World Use Case / Trade Flow Mapping | How a gas forward is priced, simulated, and settled in Endur |

---

## 📚 Level 1 – Commodities Fundamentals

|Topic|Description|
|---|---|
|Forward Contracts|Physical vs Financial, Pricing, Delivery|
|Futures|Exchange-traded, margining|
|Options|Vanilla, Asian, pricing models|
|Swaps|Fixed-floating, commodity swaps|
|Trade Lifecycle|Trade → Confirmation → Settlement|
|Price Curves & Indices|Basis, shaping, volatility surfaces|
|Valuation|MTM, fair value|
|Risk Metrics|Delta, VaR, PnL attribution|
|Hedging Strategies|Physical asset hedge, financial hedge|

---

## 🛠️ Level 2 – Endur System Mapping

|Area|Description|
|---|---|
|Deal Types & TranSubTypes|How instruments are captured|
|Deal Entry Screens|Key fields and tabs|
|Index Curves (idx_def)|How pricing is driven|
|Simulations|What simulations run and where|
|Report Tables|Key tables: `ab_tran`, `risk_sim_result`, `trading_pnl`|
|Instruments|Representation of forwards, futures, options, swaps|
|Valuation Engine|How PnL/MTM is calculated|
|PnL Attribution Reports|How Endur splits PnL|
|Curve Management|Shaping, settlement rules, calibration|
|Event Processing|Cashflows, invoices, settlements|
|Reference Data|Counterparties, commodities, books, etc.|

---

## 🧪 Level 3 – Real-World Trade Use Cases

|Use Case|Concepts & Endur Topics Covered|
|---|---|
|Gas Physical Forward|Deal entry, volume schedule, pricing, simulation|
|Power Financial Swap|Fixed-float logic, index setup, reporting|
|Crude Oil Basis Swap|Multiple indices, shaping, delta simulation|
|Hedging a Physical Gas Asset|Hedging instruments, curve usage, VaR|
|Trade Lifecycle (Physical Gas)|From entry to invoicing in Endur|
|Daily PnL Reporting Flow|MTM, realized/unrealized, PnL attribution|
|Risk Simulation & VaR Calculation|Risk scenarios, result tables, simulation config|

---

## 📅 Suggested Learning Cadence

|Week|Focus|
|---|---|
|1|Forwards + Forward Deal Type|
|2|Swaps + Swap Representation in Endur|
|3|Indices + Curve Shaping in Endur|
|4|VaR + Risk Simulations in Endur|
|5|Trade Lifecycle + Physical Gas Flow|
|6|PnL Attribution + Reporting Tables|
|7|Hedging Strategy + Real Trades Mapping|