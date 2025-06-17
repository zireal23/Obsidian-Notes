# 🧾 Forward Deal Type (Openlink Endur)

This note explains how **Forward Contracts** are modeled in Openlink Endur, with quick reference definitions included for each field or concept.

---

## 🧩 Deal Configuration in Endur

| Field                     | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `Tran Type`              | **Transaction Type** — should be set to `Forward` to classify the deal.     |
| `Tran Sub Type`          | Subcategory like `Fixed`, `Floating`, or `Index-based` pricing.             |
| `Buy/Sell`               | Whether you’re buying or selling the commodity.                             |
| `Counterparty`           | The external entity you're trading with.                                    |
| `Location`               | Physical delivery point (e.g., Henry Hub, NBP).                             |
| `Commodity`              | The traded item (Gas, Power, Oil, etc.).                                    |
| `Start Date`             | When the delivery or contract begins.                                       |
| `End Date`               | When the delivery or contract ends.                                         |
| `Volume`                 | Quantity traded (e.g., per day or total).                                   |
| `Price`                  | Agreed price per unit (can be fixed or linked to index).                    |
| `Settlement Method`      | How it's settled — `Cash` (financial) or `Physical` (delivery).             |
| `Delivery Required`      | A flag to indicate if physical scheduling is needed.                        |
| `Pricing Formula`        | Used for index deals; defines how price is calculated.                      |
| `Unit of Measure`        | e.g., MMBtu (gas), MW (power), Barrels (oil).                              |
| `Currency`               | Currency of pricing (e.g., USD, EUR).                                       |
| `Portfolio / Book`       | Internal structure for organizing trades by strategy or desk.               |

---

## 📌 Key Concepts (with Quick Definitions)

### 📦 Physical vs. Financial Forwards
- **Physical Forwards**: You take/give delivery of the commodity.
- **Financial Forwards**: Settled in cash based on price difference at maturity — no physical delivery.

🧠 **Endur Handling**: Controlled by the `Settlement Method` and whether `Delivery Required` is set to true. If physical, it activates scheduling and nominations.

---

## 🔁 Lifecycle Events in Endur

| Event Type         | Description                                                               |
| ------------------ | ------------------------------------------------------------------------- |
| `Pricing Event`    | When Endur recalculates the deal's value (e.g., when a curve is updated). |
| `Nominations`      | Sends delivery instructions to the scheduler (only for physical deals).   |
| `Settlement Event` | Generates payment instructions or delivery confirmations.                 |
| `Closeout`         | Closing or terminating the deal manually or automatically.                |

---

## 🧪 Example Forward Deal Snapshot

```yaml
Deal ID: 450123
Tran Type: Forward
Tran Sub Type: Fixed
Commodity: Natural Gas
Start Date: 2025-07-01
End Date: 2025-07-31
Price: 3.25 USD/MMBtu
Volume: 1,000 MMBtu/day
Settlement: Physical
Location: Henry Hub
Counterparty: XYZ Energy
```
## 🧠 Notes on Supporting Concepts

- **Pricing Index**: For floating deals, you reference an index (e.g., Henry Hub Daily Index).
    
- **Forward Curve**: Market data used to value forwards on any given date.
    
- **Deal Blotter**: Interface in Endur to view and filter all deals.
    
- **Book**: Internal grouping of trades (e.g., by desk, trader, or strategy).
    
- **Scheduling**: Logistics of making or receiving physical delivery.
    
- **Market Manager**: Where curves are managed and loaded into Endur.
    
- **Settlement Instructions**: Define how payment flows should occur.
    

---

## 🔗 Linked Notes

- [[Forward and Futures Contracts.md]]
    
- `[[03_Endur_Deal_Models/Deal_Lifecycle_Flow]]`
    
- `[[03_Endur_Deal_Models/Scheduling_Module]]`
    
- `[[04_Risk_Models/Forward_Pricing_and_MtM]]`
    
- `[[01_Commodities_Fundamentals/Natural_Gas_Basics]]`
    

---

## 🛠 Endur Modules Used

|Module|Role|
|---|---|
|📄 Deal Entry|Input the trade and configure fields.|
|🧾 Pricing|Calculates the value using market curves and formulas.|
|🗂 Scheduling|For physical deals, triggers nominations and delivery.|
|💸 Settlements|Produces cashflows or delivery confirmations.|
|📈 Market Manager|Manages forward curves and price data.|
|📊 Simulation|Used for valuation, risk, and reporting analysis.|