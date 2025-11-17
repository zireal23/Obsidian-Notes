## 📒 Endur: Understanding `index_historical_prices` and Reset Mechanics

### 🩶 Purpose of `index_historical_prices`

Stores **historical price fixings for indices** (gas, power, FX, IR rates) for:

- Deal pricing
    
- Floating leg resets
    
- Valuation (MTM)
    
- Historical PnL explanations
    

---

### 🔹 Key Fields:

- **`reset_date`**: The date the price fixing is **applicable to the deal for valuation/settlement**, **NOT** when the price was entered into the system.
    
- **`start_date` (RFIS Date)**: The **date the price was published/determined**, typically:
    
    - For monthly indices: last business day of the preceding month.
        
    - For daily indices: the date itself.
        
- **`ref_source`**: Pricing source (e.g., Platts, Argus).
    
- **`price/rate`**: The actual fixing used for reset.
    

---

### 🔹 Monthly vs. Daily Indices:

|Aspect|Monthly Index|Daily Index|
|---|---|---|
|**Price Publication**|Last business day of preceding month (e.g., Bidweek)|Same day|
|**Start Date**|Publish date (e.g., 2025-07-31 for Aug price)|Same as reset date|
|**Reset Date**|Each day in delivery month|Same day|
|**Fixing Usage**|Same price across month|Daily varying prices|

---

### 🩶 Reset Tab in Deals

Displays and controls how **floating price fixings apply to deals**.

Key fields:

- **Reset Date**: The date the deal expects the fixing for pricing and settlement.
    
- **RFIS Date**: Populated from `start_date` in `index_historical_prices` (when price was determined).
    
- **Price**: Pulled from `index_historical_prices` during reset.
    
- **Ref Source, Index, Volume**: Contextual data for pricing the reset.
    

---

## 🔹 Reset Processing in Endur:

1️⃣ On reset processing:

- Endur matches:
    
    pgsql
    
    CopyEdit
    
    `deal.reset_date = index_historical_prices.reset_date AND deal.ref_source = index_historical_prices.ref_source AND deal.index = index_historical_prices.index`
    

2️⃣ Pulls `price/rate` and `start_date`.  
3️⃣ Applies fixing to deal for:

- MTM
    
- Cashflow calculation
    
- Settlement generation  
    4️⃣ Populates RFIS Date in the deal’s reset record for traceability.
    

---

## 🔹 How Reset Date is Determined for Monthly Deals

✅ **Daily Delivery, Monthly Price:**

- **Reset Date = each delivery day.**
    
- Same monthly price fixing applied across all delivery days.
    

✅ **Monthly Financial Deals:**

- Single Reset Date:
    
    - Typically the **last business day of the pricing month**, or
        
    - The **day when the fixing is published**,
        
    - Based on your system configuration.
        

---

## 🩶 **Your Doubts & Answers**

### ❓ “Reset date in historical table is the date when the price was entered into the system?”

✅ **No**; it is **the date the price fixing applies for the deal for valuation and settlement.**

---

### ❓ “Reset date in the reset tab of a deal is the date when the fixing is applied to the deal?”

✅ **Correct**; it indicates when a floating price fixing will apply to the deal’s delivery/valuation.

---

### ❓ “For daily indices, start date = reset date, right?”

✅ **Yes**, for daily indices:

bash

CopyEdit

`start_date = reset_date = the date for which the price is published and applied.`

---

### ❓ “The RFIS date or start date is simply the date when the index publishes its price, usually the last trading date of the preceding month for the succeeding month?”

✅ **Correct** for monthly indices:

- E.g., Platts Bidweek for August 2025 published on 2025-07-31.
    
- `start_date = RFIS date = 2025-07-31`.
    

---

### ❓ “Reset date is basically the fixing date that calculates the payment, so a daily delivery deal has daily resets, and a monthly delivery deal has monthly resets. How is the reset date determined for monthly deals?”

✅ Correct understanding. For **monthly deals**:

- **Daily physical delivery deals** will still have **daily reset dates using the same monthly fixing.**
    
- **Financial monthly deals** will have **a single reset date** (typically last business day of the month or when the fixing is published).
    

---

## 🚩 Key Takeaways:

✅ `reset_date` = fixing application date for valuation/settlement.  
✅ `start_date` = fixing determination/publish date.  
✅ Daily delivery + monthly index = daily resets using the same price.  
✅ Daily indices = `start_date = reset_date`.  
✅ Financial monthly deals = one reset at month-end or fixing date.

## 🩶 **RFIS Date (Start Date) vs Reset Date**

|**Aspect**|**RFIS Date / Start Date**|**Reset Date**|
|---|---|---|
|**What it is**|The **date the price was published/determined by the index.**|The **date the fixing is applied to the deal to calculate cashflows, MTM, and settlement.**|
|**Stored in**|`start_date` field in `index_historical_prices`, also populated in deal’s Reset Tab|`reset_date` in `index_historical_prices` and deal’s Reset Tab|
|**Example for Monthly Index**|Platts Bidweek for Aug 2025 published on 2025-07-31 → start_date = 2025-07-31|Applied to deliveries on 2025-08-01 to 2025-08-31 → reset_dates = 2025-08-01, 2025-08-02, ..., 2025-08-31|
|**Example for Daily Index**|Price for 2025-08-15 published on 2025-08-15 → start_date = 2025-08-15|Applied on 2025-08-15 → reset_date = 2025-08-15|
|**Purpose**|**Traceability and audit of when price was determined by the index.**|**Defines the pricing application date for deal valuation and settlement.**|

---

## ✅ ✅ **Summary for your Endur notes:**

> **“RFIS Date (start_date) = The date the price was published by the index.  
> Reset Date = The date the price was applied on the deal to calculate the cashflow.”**

---

## 🩶 Why is this separation important in Endur?

✅ For **audit & compliance**:

- You know **when the market data became available** (start_date).
    
- You know **when it was used in your deals** (reset_date).
    

✅ For **valuation and settlement accuracy**:

- Multiple deals with different delivery/reset structures can use the **same fixing (same start_date) but on different reset dates**.
    

✅ For **backfills & corrections**:

- If a price was published late but is applicable retroactively, you can store:
    
    - `start_date = publish date`
        
    - `reset_date = applicable date`