## 🌐 1. Context — Why These Periods Exist

In Openlink **Endur**, most financial or physical deals (swaps, forwards, options, etc.) have some kind of _time structure_ — e.g., a gas swap that fixes every month for a year, or a power forward that delivers daily.

To model this, Endur divides a deal’s life into **periods** — units of time that drive cashflow generation, pricing, and risk.

Two important kinds of periods are:

- **Profile Periods** — define _delivery or accrual timeframes_.
    
- **Reset Periods** — define _pricing or fixing timeframes_.
    

---

## 📆 2. Profile Periods

### 🔹 Meaning

Profile periods define **when the underlying commodity (or notional exposure)** applies — in other words, _when the deal is active or delivering_.

For example, in a gas or power swap:

- You may have monthly deliveries (Jan, Feb, Mar...).
    
- Each month is a **profile period**.
    

### 🔹 Usage

Profile periods determine:

- The **delivery schedule** or accrual periods.
    
- How notional quantities are applied (e.g., 10,000 MWh per month).
    
- **Cashflow dates** (settlement typically after each profile period ends).
    
- What appears in the **Cashflow** and **Delivery Profile** tabs.
    

### 🔹 Example

You enter a 1-year monthly swap from **Jan 2026 to Dec 2026**:

- Profile periods: 12 (Jan, Feb, …, Dec).
    
- Endur will create 12 rows for each delivery month — used for volume, settlement, etc.
    

---

## 🔁 3. Reset Periods

### 🔹 Meaning

Reset periods define **when and how the floating price (or rate) is determined**.

They are relevant when the deal’s price depends on an **index or reference** that resets periodically — e.g., gas index, LIBOR, Brent, etc.

### 🔹 Usage

Reset periods determine:

- When the **price fixing** occurs.
    
- How often a rate or index is **reset** (daily, monthly, quarterly).
    
- The **averaging period** for an index (if applicable).
    
- The **valuation timeline** for MTM (mark-to-market) and risk (since pricing relies on fixings).
    

### 🔹 Example

Let’s say:

- You have a monthly swap on TTF gas.
    
- The price is the _average of daily TTF DA prices during each month_.
    

Then:

- **Profile Periods**: Monthly (delivery months)
    
- **Reset Periods**: Daily (each fixing day within that month)
    

That means:

- For January, you deliver Jan gas volumes (profile).
    
- But the floating price for January is the _average of 31 daily fixings_ (resets).
    

---

## ⚖️ 4. Key Difference

|Concept|Profile Period|Reset Period|
|---|---|---|
|**Represents**|Delivery or accrual window|Pricing or fixing window|
|**Applies to**|Quantities and cashflows|Price determination|
|**Used for**|Physical delivery, settlement|Floating rate/index calculations|
|**Example (Gas Swap)**|Monthly delivery months|Daily or monthly fixings|
|**Example (Interest Rate Swap)**|Coupon periods|LIBOR reset periods|
|**Impact on PnL**|Defines when revenue/cost realized|Defines price used to compute it|

---

## 🧩 5. Relationship Between Them

- Usually, **each profile period has one or more reset periods** within it.
    
- The structure is often:
    
    `Deal   ├── Profile Period 1 (Jan)   │      ├── Reset 1 (Jan 1–Jan 31)   │   ├── Profile Period 2 (Feb)          ├── Reset 2 (Feb 1–Feb 28)`
    
- But they can differ:
    
    - Some financial swaps have _quarterly resets but semiannual profiles_.
        
    - Some physical commodity swaps have _daily resets but monthly profiles_.
        

---

## 📊 6. Why It Matters in Endur

These periods impact:

1. **Revaluation (EOD Reval / MtM)** — Resets determine what is fixed vs. floating.
    
2. **Risk reports (Delta, Vega, etc.)** — The reset schedule determines exposure granularity.
    
3. **Cashflows / Settlements** — Profile periods drive cashflow dates.
    
4. **Back-office processes** — E.g., settlement instructions align with profile periods.
    
5. **PNL Explain / PnL Attribution** — Changes in forward curves affect future reset periods’ value.
    

---

## 💡 7. Example to Tie It Together

Let’s take a simple **Monthly Floating vs Fixed Gas Swap (Jan–Mar 2026):**

|Month|Delivery Volume|Fixed Price|Floating Index|Index Averaging|
|---|---|---|---|---|
|Jan-26|10,000 MWh|50 €/MWh|TTF DA|Daily|
|Feb-26|10,000 MWh|50 €/MWh|TTF DA|Daily|
|Mar-26|10,000 MWh|50 €/MWh|TTF DA|Daily|

- **Profile Periods** = Jan, Feb, Mar (monthly deliveries)
    
- **Reset Periods** = Daily within each month (pricing days)
    

Each month’s floating price = average of daily TTF prices  
Each month’s cashflow = (Avg Floating Price – Fixed Price) × Volume