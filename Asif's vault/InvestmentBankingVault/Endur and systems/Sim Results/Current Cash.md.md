**Concept Overview:**  
In Openlink Endur, simulation results (Sim Results) are computed when you run simulations — for example, during EOD (End-of-Day) or ad-hoc PnL analysis. These simulations produce result values such as _Base Cash_, _Avg Projection_, _Current Cash_, etc., which represent different aspects of deal cashflows and valuations.

**What “Current Cash” means:**

- **Current Cash** represents **cashflows that have _already occurred_ since the last EOD results were saved**.
    
- It effectively captures the _realized_ portion of cash movements that have taken place after the previous simulation run but before the current one.
    
- When an EOD simulation is run, all cashflows up to that point are booked into accounting or marked as realized. However, during the next trading day, some additional cash movements (e.g., payments, settlements, unwinds) may happen _before_ the next EOD run.
    
- Those newly realized cashflows (between the last saved sim result and now) are captured as **Current Cash**.
    

**Example Scenario:**

- Let’s say you ran your EOD simulation yesterday at 6 PM, which saved results up to that point.
    
- This morning, a payment related to a trade (say, a daily gas flow settlement) occurred at 9 AM.
    
- When you now rerun the simulation intraday, Endur recognizes that this payment occurred _after_ the last saved result, so it categorizes it as **Current Cash**.
    

This ensures that your total PnL properly distinguishes between:

- **Unrealized Cashflows** (future settlements not yet occurred)
    
- **Base Cash** (cashflows realized and already saved in the last EOD)
    
- **Current Cash** (cashflows realized _since_ the last EOD)
    

So, **Current Cash = Realized cashflows since last saved simulation results**.

---

### 🗒️ Obsidian Note: _Endur Simulation Result — Current Cash_

**Title:** `Endur Sim Result - Current Cash`

**Tags:** `#endur #simulation #pnl #cashflow`

---

#### 🧩 Definition

**Current Cash** represents cashflows that have _occurred since the last saved EOD simulation results_. It captures realized movements that happened after the previous simulation run.

---

#### 🧠 Concept

- Endur’s simulations (like EOD) store result snapshots — e.g., Base Cash, NPV, Delta, etc.
    
- When new cash movements occur _after_ that snapshot but before the next EOD run, those are reported as **Current Cash**.
    
- It helps isolate recent realized cash activity from prior EOD data and upcoming projections.
    

---

#### 📊 Example

|Time|Event|Classification|
|---|---|---|
|Oct 5, 6 PM|EOD Simulation run and saved|Base Cash updated|
|Oct 6, 9 AM|Physical gas payment settled|Current Cash (since after last EOD)|
|Oct 6, 6 PM|Next EOD Simulation run|Current Cash merged into Base Cash|

---

#### 🧾 Formula (Conceptual)

`Current Cash = Cashflows realized since the timestamp of the last saved sim result`

---

#### 🧩 Relation to Other Sim Results

| Sim Result         | Meaning                                      |
| ------------------ | -------------------------------------------- |
| **Base Cash**      | Realized cashflows saved during last EOD run |
| **Current Cash**   | Cashflows realized since last EOD            |
| **Projected Cash** | Future-dated cashflows yet to occur          |