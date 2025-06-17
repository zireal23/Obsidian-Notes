# {{ Forwards }}

# 📘 Forward Contracts

## 🧠 Overview

A **forward contract** is a privately negotiated agreement between two parties to buy or sell a specific commodity at a **fixed price** on a **future date**. These are **over-the-counter (OTC)** instruments and are widely used in commodity markets.

- 📆 Future-dated agreement
- ⚙️ Custom terms (volume, price, location, date)
- 🔄 Settled either by **delivery** (physical) or **cash** (financial)
- 🎯 Commonly used for **hedging** or **speculation**

---

## 🧮 Pricing a Forward Contract

In commodities, pricing accounts for several real-world factors:

### 💡 General Formula:
Forward Price = Spot Price + (Cost of Carry - Convenience Yield)
For a storable commodity: F = S × e^(r + s - c) × T

Where:
- `F` = Forward Price  
- `S` = Spot Price  
- `r` = Risk-free rate  
- `s` = Storage cost (annualized)  
- `c` = Convenience yield (benefit of holding the physical good)  
- `T` = Time to maturity (in years)

📌 *Convenience yield* is crucial in commodities. It reflects the value of holding the physical good (e.g. ensuring supply, avoiding shortage).

---

## ⚙️ Real-World Use Cases

### ✅ Hedging:
A utility company enters into a forward contract to **buy natural gas** in six months at a fixed price, insulating itself from price spikes.

### 📈 Speculation:
A trading desk sells forwards anticipating a drop in commodity prices.

---

## 🧩 Endur Representation

### 🎯 Deal Type
- `tran_type`: `Forward`
- `tran_sub_type`: `Fixed Price`, `Floating`, `Index-based`

### 📑 Key Fields
| Field                 | Description                         |
|----------------------|-------------------------------------|
| Start Date / End Date| Delivery period                     |
| Price                | Agreed forward price                |
| Quantity             | Total volume or delivery profile    |
| Settlement Method    | Physical or Cash                    |
| Delivery Location    | Pipeline, hub, terminal, etc.       |

### ⚙️ Additional Configuration
- **Index-linked forwards** use internal or market curves.
- **Pricing components** may be configured with formulas.
- **Physical flag** in deal determines if it's to be delivered.
- Triggers and events tie into scheduling (Nomination, Delivery).

---

## 📉 Risk Metrics
- **Market Risk**: Exposure to spot/forward curve changes
- **Credit Risk**: Counterparty default (especially in bilateral deals)
- **Liquidity Risk**: OTC contracts may not be easily offset

---

## 💡 Notes & Diagrams

### Example: Natural Gas Forward
- Start Date: July 1
- End Date: July 31
- Volume: 1000 MMBtu/day
- Price: $3.25/MMBtu
- Settlement: Physical
- Delivery: Henry Hub

---
## 🏦 Deal Capture & Booking in Investment Banks (with Traders Desk + Marketers Desk)

### 💡 Who's Who?

|Role|Responsibility|
|---|---|
|**Marketers (Sales Desk)**|Face clients. Pitch products, negotiate indicative pricing, and bring in orders.|
|**Traders (Trading Desk)**|Price risk, execute trades, and manage the bank’s risk positions.|
|**Middle Office**|Validate trade details, ensure compliance, and check risk.|
|**Back Office**|Handles settlement, reconciliation, and accounting.|

---

## 🔄 Typical Workflow

Let’s go through a **step-by-step trade flow** for a commodity forward contract:


### **1. Client Request / Quote (Initiated by Marketing Desk)**

📌 **What Happens:**

- A **client reaches out** to the marketer to lock in a future price for a commodity.
    
- Marketer engages the **trader** to get pricing based on the forward curve and risk appetite.
    
- The trader provides a **quote** to the marketer.
    

🛠 **Endur / Internal System:**

- Not yet in Endur.
    
- May use Excel, pricing tools, or custom quoting systems.
    
- Some systems integrate quoting directly with Endur or external APIs.
    

---

### **2. Deal Agreement & Term Sheet**

📌 **What Happens:**

- Marketer and client agree to terms: quantity, price, settlement date, delivery point.
    
- The trader signs off on risk/pricing.
    
- A term sheet or confirmation is drafted.
    

🔒 **Internal Controls:**

- **Pre-deal checks**: credit limits, KYC/AML, and onboarding must be in place.
    

---

### **3. Deal Capture (Booking)**

📌 **What Happens:**

- The deal is **entered into the system of record**, often by:
    
    - The **trader** directly
        
    - A **middle-office trade capture analyst**
        
    - The **marketer**, in some setups
        

🛠 **Endur / ETRM System:**

- Entered as a **Forward Physical Deal** or **OTC Derivative Deal**.
    
- Key fields captured:
    
    - Deal type (physical/financial)
        
    - Underlying (e.g., Brent, Henry Hub)
        
    - Quantity, price
        
    - Counterparty
        
    - Trade book
        
    - Location, delivery terms
        
    - Start/End dates
        
    - Reference to marketer/salesperson
        

🔐 **Internal Audit Trail:**

- Who entered the deal, when, and approval history.
    

---

### **4. Trade Validation & Enrichment**

📌 **What Happens:**

- **Middle office** validates trade inputs for:
    
    - Trade limits
        
    - Pricing consistency
        
    - Legal terms
        
    - Regulatory requirements
        

🛠 **In Endur:**

- Trade moves through a **workflow engine**.
    
- Status updates: _Captured → Validated → Confirmed_.
    

---

### **5. Confirmation & Allocation**

📌 **What Happens:**

- The client receives a trade confirmation (manual or electronic).
    
- Allocations happen if the trade is part of a block trade.
    

🛠 **In Endur:**

- Uses **confirmation module** or external matching tools (e.g., ICE eConfirm, MarkitWire).
    
- Allocations may generate child trades from a block.
    

---

### ✅ Summary: Roles in Deal Capture

|Step|Marketing Desk|Trading Desk|Middle Office|
|---|---|---|---|
|Client engagement|✔️|✖️|✖️|
|Pricing request|✔️ → via trader|✔️ (provides price)|✖️|
|Deal agreement|✔️ (with client)|✔️ (approves risk)|✖️|
|Deal booking|✔️/✖️ (if allowed)|✔️|✔️ (sometimes captures)|
|Validation|✖️|✖️|✔️|
|Confirmation|✔️ (sends to client)|✖️|✔️ (tracks/matches)|

---

## 🧠 Important Considerations

- **Segregation of Duties**: Booking, validation, and confirmation are separated to reduce risk.
    
- **Auditability**: Every action (quote, booking, modification) is logged and timestamped.
    
- **Integration with ETRM**: Endur may be integrated with pricing tools, Excel plugins, or internal CRM systems to speed up trade booking.

---

## 🔄 Realistic Walkthrough: **Natural Gas Physical Forward Contract**

### 🎯 Scenario

> A **trader at ABC Commodities** sells 30,000 MMBtu of **Henry Hub Natural Gas** to **XYZ Utilities** for delivery in **July 2025**, at a **fixed price of $2.90/MMBtu**.

- Delivery Location: Henry Hub
    
- Delivery Dates: 1–31 July 2025
    
- Price: Fixed at $2.90
    
- Volume: 1,000 MMBtu/day
    

---

## 🔁 Step-by-Step Lifecycle with Endur Mapping

### 1. 📥 **Deal Capture**

**Trader or Marketer** enters the deal into Endur:

- **Instrument**: _Physical Forward (Natural Gas)_
    
- **Buy/Sell**: Sell
    
- **Counterparty**: XYZ Utilities
    
- **Volume**: 1,000 MMBtu/day
    
- **Price**: $2.90 (Fixed)
    
- **Delivery Dates**: 2025-07-01 to 2025-07-31
    
- **Delivery Point**: Henry Hub
    

🔧 **Endur Module**:

- Deal Entry Screen → `Tran Info` tab for metadata
    
- `Volume Profile` defines daily quantities
    

---

### 2. ✅ **Deal Validation**

**Middle Office** reviews:

- Deal terms and counterparty limits
    
- Credit exposure check (credit engine)
    
- Pricing logic validation
    

✔️ Status changed to: `Validated`

🔧 **Endur Workflow**:

- Configured validation workflows
    
- Auto-validation rules (for liquid counterparties/products)
    

---

### 3. 📊 **Risk & Valuation**

**Risk Management** performs:

- **MTM** calculation vs. forward curve (e.g., Platts HH Futures)
    
- **VaR simulations**
    
- P&L Sensitivities (via `Sim Result`)
    

🔧 **Endur**:

- Uses market curves (e.g., `HH_Gas_Forward_Curve`)
    
- Sim Result Viewer (Delta, MTM, Greeks)
    
- Shows exposure in trader’s portfolio
    

---

### 4. 🛡 **Hedging (Optional)**

Trader might enter a hedge:

- **Buy a NYMEX HH Futures Contract** for July 2025
    
- Matched volume: 1,000 MMBtu/day
    
- Purpose: Offset the forward exposure
    

🔧 In Endur:

- Auto-booking rules might capture this hedge
    
- The hedge is **linked** to the original client trade
    
- Portfolio-level netting shows zero net position
    

---

### 5. ⚙️ **Operations Setup (Logistics)**

As July approaches, the **scheduling team**:

- Confirms nomination instructions with XYZ Utilities
    
- Ensures pipeline capacity at Henry Hub
    
- Adjusts volumes if needed (e.g., force majeure, client revision)
    

🔧 Endur Ops Console:

- `Scheduling Tab` for each transaction leg
    
- Tracks status: Nominated, Scheduled, Confirmed
    
- Includes transport instructions (if managed internally)
    

---

### 6. 💸 **Settlement & Invoicing**

On delivery dates (e.g., July 31):

- 31 deliveries x 1,000 MMBtu = 31,000 MMBtu
    
- Invoice amount = 31,000 x $2.90 = **$89,900**
    

**Settlements Team**:

- Confirms delivery quantity
    
- Generates invoice (PDF, EDI, SWIFT)
    
- Triggers cash flow in Endur
    

🔧 Endur:

- **Settlement Instructions** tab
    
- Uses delivery profile to calculate invoice
    
- Triggers payment via integration with treasury systems
    

---

### 7. 🧾 **Accounting Entries**

**Endur Accounting Module** generates:

- Revenue recognition: Cr. Sales / Dr. Receivables
    
- Inventory updates (if using internal gas)
    
- FX entries if multi-currency
    

🔧 GL Interface:

- Entries exported to SAP, Oracle, etc.
    
- Reconciliation reports ensure no discrepancies
    

---

### 8. 📅 **Actualization & Close**

After July ends:

- Actual quantities matched with scheduled volumes
    
- Deal marked as **actualized**
    
- P&L locked for accounting close
    

🔧 Endur Actualization Module:

- Matches scheduled vs. delivered quantities
    
- Finalizes cash flows, P&L
    

---

## 📌 Recap of What Happened

|Phase|Real-World Step|Endur Module|
|---|---|---|
|1. Capture|Trade Booked|Deal Entry|
|2. Validate|Deal Reviewed|Workflow Engine|
|3. Analyze|Risk Simulations|Sim Result|
|4. Hedge|Futures Entered|Auto-book / Manual Deal|
|5. Operate|Delivery Scheduled|Ops Console|
|6. Settle|Invoice Sent|Settlements Tab|
|7. Account|Revenue Booked|Accounting Interface|
|8. Finalize|Deal Closed|Actualization|
