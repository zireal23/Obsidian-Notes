## 🧩 Volatility Effective Input (Simulation Result) — Openlink Endur

### 📘 Overview

The **Volatility Effective Input** simulation result (`VOL_EFF_INPUT_RESULT`, Result ID `169`) represents the _final volatility values_ that Endur actually used during pricing or simulation runs.  
It captures the **effective volatility surface** after all primary and adjustment matrices have been combined based on their definitions.

---

### 🧮 What It Contains

Each row in this sim result corresponds to a **single gridpoint** on a volatility surface — defined by expiry and strike (or moneyness).  
The result shows the _effective volatility_ applied at that gridpoint for that particular simulation.

**Key idea:**

> Effective volatility = Primary matrix + (or ×) Adjustments  
> depending on whether the volatility definition is additive or multiplicative.

---

### ⚙️ How Endur Computes the Effective Volatility

1. **Primary Volatility Matrix**  
    This is the base matrix (e.g., expiry vs moneyness) defined in the volatility definition.
    
2. **Adjustment Matrices (Secondary / Tertiary)**
    
    - Can adjust the vol surface seasonally or for term-structure effects.
        
    - Applied additively or multiplicatively.
        
3. **Combination Rules**
    
    - If adjustment shares the same grid structure as the primary → Endur merges them directly.
        
    - If the adjustment has a different grid structure → Endur interpolates and maps it onto the primary.
        
    - Exception: when secondary adjustment is _calendar-basis_, the adjustment’s own grid structure can become the base.
        
4. **Output**  
    The result returned is the _final combined vol matrix_ used for pricing — each gridpoint after all adjustments applied.
    

---

### 👁️ Viewing Volatility Results in Endur UI

**Path:**  
`Results → Gen Results → VOL_EFF_INPUT_RESULT`

**Steps to interpret:**

1. Filter by `Result ID = 169` or “Volatility Effective Input”.
    
2. Key columns:
    
    |Column|Description|
    |---|---|
    |`disc_index`|ID of the volatility definition used|
    |`id1`, `label1`|Expiry gridpoint (e.g. 1M, 6M, 1Y)|
    |`id2`, `label2`|Strike or moneyness gridpoint|
    |`date1`, `date2`|Associated date labels|
    |`result`|Effective volatility (decimal, e.g., 0.35 = 35%)|
    |`dimension_id`|0 = Primary, 1/2 = Adjustment layers|
    
3. To view **volatility names instead of blank IDs:**
    
    - Open **Configure** in Gen Results.
        
    - Change “parameter one” to `Volatility_Table`.
        
    - Apply → now the `disc_index` column will show the volatility name.
        

---

### 🧾 Example Row Interpretation

|disc_index|id1|label1|id2|label2|date1|dimension_id|result|
|---|---|---|---|---|---|---|---|
|42|5|1M|10|100%|2025-12-01|0|0.403|

**Interpretation:**

- Vol definition ID `42` (map to name via `volatility_table`).
    
- Gridpoint = **1-month expiry**, **ATM strike (100%)**.
    
- `dimension_id = 0` → Primary matrix row.
    
- `result = 0.403` → Effective volatility of **40.3%** used in pricing.
    

---

### 🧑‍💻 SQL Example — Querying from Database

`SELECT   gr.sim_run_id,   gr.result_id,   gr.disc_index AS volatility_id,   v.vol_name,   gr.id1,   gr.label1,   gr.id2,   gr.label2,   gr.date1,   gr.date2,   gr.dimension_id,   gr.result AS effective_vol FROM gen_result gr LEFT JOIN volatility_table v ON v.vol_id = gr.disc_index WHERE gr.result_id = 169  -- VOL_EFF_INPUT_RESULT   AND gr.sim_run_id = :sim_run_id ORDER BY v.vol_name, gr.id1, gr.id2, gr.date1;`

**Notes:**

- Replace `volatility_table` with your actual schema/table name.
    
- `result` column stores the final effective vol (decimal format).
    
- `dimension_id` identifies whether it’s a primary or adjustment dimension.
    

---

### ⚠️ Common Pitfalls & Debugging Tips

|Issue|Cause|Fix|
|---|---|---|
|Vol name shows blank|`disc_index` formatted as `INDEX_TABLE`|Change parameter to `Volatility_Table`|
|Values differ from trader sheets|Different interpolation, multiplicative/additive mismatch|Verify definition setup and vol conversion base|
|Gridpoints mismatch|Adjustment has different grid|Check which structure Endur used (primary vs secondary)|
|Dates off by one|Label mismatch|Verify date mapping in vol definition|
|Duplicate rows|Multiple dimensions (0, 1, 2) returned|Filter by `dimension_id=0` for effective result|

---

### 🎯 Practical Use Cases

- **Validate pricing inputs:** confirm the exact vol grid Endur used in deal valuation.
    
- **Audit trail:** reproduce valuations by reusing the same effective vol set.
    
- **PnL Explain:** link day-to-day PnL movement to changes in vol inputs.
    
- **Vega Sensitivities:** revalue portfolio with shifted vols to get exposure.
    
- **Debug adjustments:** verify seasonal or calendar-based vol adjustments were applied correctly.
    

---

### 🔍 Troubleshooting Checklist

1. Map `disc_index` → vol name using `volatility_table`.
    
2. Review volatility definition setup (primary, adjustments, additive/multiplicative).
    
3. Verify latest market data loaded.
    
4. Filter Gen Results by `dimension_id` for clarity.
    
5. If numbers look off → rerun targeted simulation and compare.
    

---

### 🧠 Key Insight

> The **Volatility Effective Input** result is the _ground truth_ of what Endur’s pricing engine actually used during a simulation or revaluation.  
> It bridges the gap between volatility definitions (setup layer) and pricing results (valuation layer), making it a critical diagnostic and auditing tool.