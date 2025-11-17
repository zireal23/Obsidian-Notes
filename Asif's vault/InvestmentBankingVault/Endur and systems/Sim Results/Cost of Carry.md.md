## 🧾 Cost of Carry (Result ID 18)

**Path:**  
`Home > Results > Cost of Carry`

---

### 🔍 Overview

- **Purpose:** Measures _how much a deal’s MTM (mark-to-market) value changes_ due to the mere _passage of time_ (typically one business day).
    
- **Conceptually:** Like _academic Theta_ — partial derivative of MTM with respect to time.
    
- **Dependencies:**
    
    - Relies on the **Current Cash Result**.
        
    - Both depend on the timing of the **prior day’s EOD Reval** (End-of-Day Revaluation).
        

Hence, Cost of Carry results can vary depending on _when_ the previous day’s EOD reval was run.

---

### 🧮 Definition

**Formula:**

Cost of Carry=(PVtomorrow−PVtoday)×(Days between today and next good business day)+Current Cash Result\text{Cost of Carry} = (\text{PV}_{\text{tomorrow}} - \text{PV}_{\text{today}}) \times (\text{Days between today and next good business day}) + \text{Current Cash Result}Cost of Carry=(PVtomorrow​−PVtoday​)×(Days between today and next good business day)+Current Cash Result

Where:

- **PVₜₒₘₒᵣᵣₒʷ** = PV (Present Value) when system date is rolled forward by one calendar day and the deal is revalued.
    
- **PVₜₒdₐy** = PV as of the current date.
    
- **Current Cash Result** = The realized cash impact from settlements or fixings up to today.
    

Effectively, this is equivalent to:

Cost of Carry≈MTM(T+1)−MTM(T)\text{Cost of Carry} \approx \text{MTM}(T+1) - \text{MTM}(T)Cost of Carry≈MTM(T+1)−MTM(T)

---

### 🧩 Result Properties

|Property|Value|
|---|---|
|**Result ID**|18|
|**Enumeration**|COST_OF_CARRY_RESULT|
|**Class**|Tran Result|
|**Toolsets**|All toolsets supported|
|**Interpretation**|Time decay (day-over-day PV change)|

---

### ⚙️ Operational Considerations

- Should be run **EOD (End-of-Day)** — after all fixings and historical prices are entered.
    
- **Intra-day runs** may produce _inconsistent_ results because fixings may be incomplete.
    
- **Hourly Curves** are **not supported**.
    

---

### 🧾 Environment Variables

#### 1. `AB_COST_OF_CARRY_ROLL_CURVES`

Controls whether curve inputs are _rolled forward_ or _kept stationary_ for the T+1 valuation.

|Setting|Behavior|
|---|---|
|**FALSE (default)**|Keeps curve output stationary → projected prices for T+1 = T (recommended for Energy Curves).|
|**TRUE**|Rolls curve inputs forward one business day → replicates pre-V8 behavior.|

> Applies only to **Energy Curves**. Other markets may still require rolling to reflect cost-of-carry dynamics.

---

### 🧾 Additional Environment Variable (Delta Handling)

#### 2. `AB_NO_DELTA_IF_HISTORIC_PRICE`

|Purpose|Controls whether delta exposure on expiring gridpoints remains visible after historical prices are entered.|
|---|---|
|**Default:** TRUE|Delta exposure is removed once a historic price is entered for the expiring gridpoint.|

**Example:**

- Nymex April contract expires March 28.
    
- If a historical price is entered for March 28, delta exposure on April rolls off immediately instead of persisting until March 29 (T+1).
    

---

### 🧮 Methodology Changes Across Versions

#### Pre-V8.0

- Approximation based on **discount curve movement** — less accurate.
    

#### V8.0 and Later

- Uses **rolled market data**:
    
    - Rolls all relevant curves forward by one day.
        
    - Re-computes PV for T+1.
        
    - Produces a more _rigorous_ and _realistic_ cost-of-carry measure.
        

To enable the new (accurate) method:

1. Go to **Admin Manager → Data Model Extension**
    
2. Open **Simulation Results Configuration**
    
3. Under **PNL Detail Attributes**, set:  
    **“Cost of Carry Roll Market Data” → Yes**
    

|Setting|Behavior|
|---|---|
|**No (default)**|Legacy method (pre-V8 behavior)|
|**Yes**|Rolls market data, recomputes PV for T+1 (more accurate)|

---

### ⚠️ Key Takeaways

- Cost of Carry measures **time decay (Theta)**, not price risk.
    
- Must be run **EOD** after fixings/historic prices.
    
- Dependent on **Current Cash Result** and **EOD timing**.
    
- Environment variables control curve rolling behavior and delta exposure logic.
    
- From V8 onwards, more precise market-data-based computation is available.