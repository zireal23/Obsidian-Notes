___
### **1. What are Commodity Futures and How Do They Work?**

- **Definition**: Standardized contracts traded on exchanges to buy or sell a specific quantity of a commodity at a predetermined price at a future date.
    
- **Key Features**:
    
    - Exchange-traded (e.g., NYMEX, ICE)
        
    - Standardized in terms of quality, quantity, and delivery
        
    - Marked-to-market daily with margin requirements
        

---

### **2. Why Are Commodity Futures Used?**

- **Hedging**: To offset price risk in physical commodity positions (e.g., an airline hedging jet fuel costs).
    
- **Speculation**: Traders take positions based on expected price movements.
    
- **Arbitrage**: Exploit pricing inefficiencies between spot and futures markets.
    

---

### **3. How Are They Used to Hedge Physical Deals in a Portfolio?**

- **Physical Position Risk**: Physical commodity deals expose an organization to price fluctuations.
    
- **Offsetting Futures**: Entering into futures contracts with inverse price exposure can neutralize this risk.
    
- **Example**:
    
    - Buy crude oil physically at a fixed price.
        
    - Sell crude oil futures to lock in today's market price for future sale.
        
- **Portfolio Level**: Hedging is often managed at a portfolio level using hedge accounting or hedge books.
    

---

### **4. How Are Futures Represented in Openlink Endur?**

- **Deal Type**: Futures are usually represented as specific deal types like “Futures” or “Exchange Traded”.
    
- **Linked to Market**: Futures prices come from market curves (e.g., ICE Brent Futures Curve).
    
- **Key Attributes**:
    
    - Contract code (e.g., CL for WTI crude)
        
    - Delivery month
        
    - Quantity
        
    - Exchange
        
    - Trade date and maturity
        
- **Margining**: Margin calls and daily mark-to-market flows are modeled separately, often in cash flows or associated transfer deals.
    

---

### **5. Lifecycle of a Futures Deal in Endur**

1. **Trade Entry**: Trader books the deal in Endur, selecting the futures product and delivery month.
    
2. **Confirmation**: Internal/exchange confirmation processes.
    
3. **Daily MTM & Margining**: Valuation updated daily. Margins calculated and settled with the clearing broker.
    
4. **Rollover or Closeout**: Futures are either rolled (offset before expiry) or closed out (settled financially or physically).
    
5. **Settlement**: Either delivery or cash settlement.
    
6. **Archiving**: After settlement, deal is archived or marked as inactive.
    

---

### **6. How is PnL and NPV Calculated for Futures?**

- **PnL**:
    
    - **Realized PnL**: From closing/offsetting positions.
        
    - **Unrealized PnL**: Change in value of open positions.
        
    - Includes daily gains/losses from MTM.
        
- **NPV (Net Present Value)**:
    
    - Sum of discounted future cash flows.
        
    - For futures, this is often zero or near-zero because of daily margining (cash settled daily).
        
    - Any carry cost or spread from curve misalignment may appear as NPV.
        

---

### **7. How is Risk Calculated?**

- **Market Risk Metrics**:
    
    - **Delta**: Exposure to price movement of underlying commodity.
        
    - **Vega**: Not typically relevant for vanilla futures.
        
    - **Scenario Analysis**: Shock the market curves (e.g., +$1, -$5) and observe PnL changes.
        
    - **VaR (Value-at-Risk)**: Quantifies potential loss over a horizon at a given confidence level.
        
- **Position Risk**:
    
    - Exposure by delivery month, contract, and commodity.
        
- **Hedge Effectiveness**:
    
    - How well the futures position offsets the risk of the physical position.


## **Section 3: Using Futures to Hedge Physical Deals**

### ✅ **Why Hedge Physical Deals?**

Physical commodity trades expose a company to **price risk**. For example:

- A refiner contracts to buy 1 million barrels of crude oil for delivery in 3 months.
    
- If oil prices rise before delivery, the refiner faces higher costs.
    
- If they lock in the price today using **futures**, they can protect themselves from that risk.
    

---

### ✅ **How Futures Hedge That Risk**

Futures contracts provide a **standardized and liquid** way to lock in prices.

#### 🔹 **Direct Hedge (1:1)**

You buy/sell a futures contract for the same commodity, same delivery month, and same quantity as your physical exposure.

**Example:**

- You plan to sell 100,000 barrels of WTI crude in September.
    
- You sell 100 lots of the **CL (NYMEX WTI)** September futures contract today.
    
- If market prices drop, the futures position gains value, offsetting your lower physical sale price.
    

#### 🔹 **Proxy Hedge (Cross-Hedge)**

Sometimes a physical deal doesn’t have an exact futures equivalent. In this case, you use a **correlated instrument**.

**Example:**

- You sell Nigerian Bonny Light crude, but there's no Bonny Light futures contract.
    
- You hedge using **Brent crude futures**, assuming Brent and Bonny Light track closely.
    

---

### ✅ **Portfolio Hedging vs Deal-Level Hedging**

#### 🔹 **Deal-Level**

Each physical deal is individually hedged with a corresponding futures position.

- Easier to track.
    
- Often used for regulatory or accounting compliance (e.g., hedge accounting).
    
- Requires precise mapping.
    

#### 🔹 **Portfolio-Level**

The trader or risk manager monitors the **net exposure** across all physical positions and hedges the **net position**.

- Reduces transaction costs and margin requirements.
    
- More flexible and scalable.
    
- Common in large trading organizations.
    

---

### ✅ **Example: Portfolio-Level Hedging**

Suppose your portfolio for July has:

|Commodity|Physical Position|Market Direction|Hedging Action|
|---|---|---|---|
|Crude Oil|Long 1,000,000 bbl|Risk if price ↓|Sell 1,000 WTI Futures|
|Natural Gas|Short 500,000 MMBtu|Risk if price ↑|Buy 500 Henry Hub Futures|

You're exposed to crude price _decreases_ and gas price _increases_ → use **futures to offset both**.

---

### ✅ **Strategic Considerations**

- **Hedge Ratio**: You might not hedge 100% of your exposure. Could be 70–90%, depending on risk appetite.
    
- **Liquidity and Cost**: Futures are generally liquid, but liquidity varies by contract and delivery month.
    
- **Basis Risk**: The risk that the hedge instrument (e.g., Brent futures) doesn't move in perfect correlation with the physical commodity.
    
- **Operational Risk**: Managing margin calls and settlement can be complex with many futures positions.
    

---

### ✅ **Endur Representation (Preview of Section 4)**

- Futures deals are linked to physical deals via **hedge books**, **strategy books**, or **internal deal linkages**.
    
- You can model a hedge relationship in Endur using custom fields or strategies that tag which futures hedge which physical trades.

## ✅ How Are Futures Marked to Market?

Futures are **marked to market daily** — this means their value is recalculated each day based on the current market price for the contract (i.e., its latest settlement price from the exchange).

---

### ⚙️ **Mark-to-Market Price = Current Futures Market Price**

> **Not the spot price**, and **not the original deal price**.

Each day:

- The exchange publishes a **settlement price** for each active futures contract (e.g., CL Sep 2025 settles at $79.50 today).
    
- This price becomes the **reference price** for MTM.
    

---

### 📉 Example of Daily MTM

Say you:

- Bought 10 lots of **WTI Sep 2025 Futures** at **$80.00**.
    
- Each lot = 1,000 barrels.
    

#### Day 1:

- Settlement price = **$79.50**
    
- MTM Loss = (79.50 - 80.00) × 10,000 = **–$5,000**
    

This loss is:

- Booked as **Unrealized PnL** in Endur
    
- Physically settled via **margin transfer** (variation margin) with the exchange/broker
    

#### Day 2:

- Settlement price = **$81.00**
    
- MTM Gain = (81.00 - 79.50) × 10,000 = **+$15,000**
    

The net PnL now is: –5,000 (day 1) + 15,000 (day 2) = **$10,000 gain**

---

## ✅ At Expiry: Cash-Settled or Physically-Settled?

### 🔹 **Cash-Settled Futures**

- Most futures contracts (e.g., Henry Hub Natural Gas) are **cash-settled**.
    
- On expiry, the **final settlement price** (set by the exchange, often based on a weighted average of spot trades) determines final PnL.
    
- Your open futures position is closed, and a final margin adjustment is made.
    
- There’s **no physical delivery**.
    

### 🔹 **Physically-Settled Futures**

- Contracts like **NYMEX WTI** or **Brent Crude** are **physically deliverable**.
    
- If not closed before expiry, you must:
    
    - Accept delivery (if long)
        
    - Make delivery (if short)
        

Most traders **roll** these contracts before expiry to avoid delivery risk.

Still, MTM is always based on **futures prices**, not spot prices.

---

## ✅ In Endur: Where Is This Reflected?

- The **current futures settlement price** is loaded into a **market curve**.
    
- Endur revalues your position daily based on this price.
    
- The difference between today’s and yesterday’s value flows into:
    
    - **MTM (Mark-to-Market) PnL**
        
    - **Cash Flow (Margin Transfer Deal)**
        
- These updates are tracked under:
    
    - `Deal View` > PnL Tab
        
    - `Cash Flow` Reports
        
    - `Risk Viewer` for exposures
        

---

## 🔍 Summary

| Concept          | Value Used                                                  |
| ---------------- | ----------------------------------------------------------- |
| Daily MTM        | **Futures contract's current market price** (from exchange) |
| Final Settlement | **Futures contract’s settlement price at expiry**, not spot |
| Spot Price       | Used in valuation of **physical** trades, not futures       |
| MTM in Endur     | Driven by **market curves**, not static trade prices        |


### ✅ Settlement Prices Are at the Index Level

When you book a futures contract, it is always tied to a specific **underlying index** published by an exchange. This index determines the **settlement price** used for:

- **Mark-to-Market (NPV)**
    
- **PnL calculation**
    
- **Final cash settlement (for cash-settled contracts)**
    

---

### 🔹 Example: Futures Contract Tied to an Index

|Contract Type|Underlying Index|Published By|
|---|---|---|
|NYMEX WTI Crude Futures|**CL** (WTI Light Sweet Crude)|CME/NYMEX|
|ICE Brent Crude Futures|**Brent** Index|ICE|
|Henry Hub Nat Gas Futures|**NG** (Henry Hub)|NYMEX/CME|
|Dutch TTF Gas Futures|**TTF** Index|ICE Endex|
|JKM LNG Futures|**JKM Platts**|Platts (via ICE)|

Each day, the **exchange publishes the official settlement price** for each contract month and index. These are the prices that Endur will use in your market curves (often populated via market data feeds).

---

### 🔸 In Openlink Endur

When booking the futures deal, you typically specify:

- **Index Name** (e.g., NG.NYMEX, TTF.ICE, etc.)
    
- **Contract Month / Delivery Period**
    
- **Quantity & UOM**
    
- **Exchange**
    

Endur uses this index to:

- Lookup the appropriate **curve and price point** in Market Manager.
    
- Drive the **revaluation and PnL** calculations.
    

You can usually find this in the deal under the `Index` or `Reference Index` field.

---

### 🧠 Important Points

- The **index drives the settlement price**, not the spot price in a physical market.
    
- Even if your futures position is meant to hedge a physical flow (e.g., LNG spot deal), its **valuation and PnL still come from the index’s published futures curve**.

## ✅ Futures Curves in Endur Are Monthly (or Periodic)

In Openlink Endur, **futures market curves** are typically modeled at a **monthly granularity**, because:

1. **Futures contracts trade for monthly delivery buckets** (e.g., "TTF Sep 2025").
    
2. **Exchanges publish one settlement price per contract month**, not daily granularity within a month.
    
3. It aligns directly with how futures are traded and settled — i.e., a single price governs the full contract month.
    

---

### 🔸 Example: TTF Futures Curve in Endur

|Delivery Month|Curve Name|Index|Settlement Price|
|---|---|---|---|
|Sep 2025|`TTF Futures`|`TTF.ICE`|€32.50|
|Oct 2025|`TTF Futures`|`TTF.ICE`|€33.10|
|Nov 2025|`TTF Futures`|`TTF.ICE`|€35.00|

Each of these points represents the **last published settlement price** for that contract from the exchange.

---

### 🔹 So When You Revalue a Futures Deal in Endur:

- The system looks up the **curve point for the corresponding delivery month** (e.g., Sep 2025).
    
- Applies that **index price** to compute NPV and PnL.
    
- Any deal delivery period shorter than a month is still valued using the full month's settlement price.
    

---

### 🧠 Why Not Daily?

Because:

- **Futures contracts don’t have daily prices per delivery day.** Only a single price is quoted for each full contract period.
    
- That’s how the underlying exchanges (e.g., CME, ICE) publish prices.
    

---

### 🧩 Behind the Scenes in Endur

- The **Market Manager** loads daily settlement prices and maps them to the corresponding **monthly curve point**.
    
- Curves like `NG.NYMEX Futures`, `JKM.Platts`, or `TTF.ICE Futures` will show 1 point per forward month.
    
- When you run `Reval`, it picks the correct point for the deal's delivery month and uses it for MTM and PnL calculations.

## ✅ The Key Insight: The **Monthly Curve Point Price _Does_ Change Daily**

Even though the **granularity** of the futures curve is monthly, the **price for that month changes every trading day**, because:

- **Exchanges publish daily settlement prices** for each **active contract month** (e.g., "TTF Oct 2025").
    
- Each day’s updated value for that monthly bucket is loaded into the Endur **market curve** — replacing the previous day’s price.
    

---

### 🔹 Example: Daily Settlement Price Changes for "TTF Oct 2025"

|Date|Monthly Bucket|Settlement Price|
|---|---|---|
|Sep 2, 2025|Oct 2025|€33.10|
|Sep 3, 2025|Oct 2025|€33.35|
|Sep 4, 2025|Oct 2025|€32.95|

So even though there is only **one curve point per month**, the value of that point **updates daily**, allowing for **daily MTM and PnL movement**.

---

## 🔹 How NPV and MTM Change Daily in Endur

Let’s say you hold a 100-lot TTF Oct-2025 future at €33.00.

|Date|Settlement Price (Oct 2025)|NPV = (Settle - Trade) × Qty × Lot Size|
|---|---|---|
|Sep 2, 2025|€33.10|(€33.10 – €33.00) × 100 × 1 MWh = €10.00|
|Sep 3, 2025|€33.35|(€33.35 – €33.00) × 100 × 1 = €35.00|
|Sep 4, 2025|€32.95|(€32.95 – €33.00) × 100 × 1 = –€5.00|

The change in price each day results in:

- A different **MTM (NPV)**
    
- A corresponding **Unrealized PnL movement**
    
- And if cleared, a **variation margin cash flow** for Realized PnL
    

---

## 🔹 In Openlink Endur: What Enables This?

1. **Market Curves** are updated daily via feeds (e.g., via Endur’s Market Manager):
    
    - Curve name: `TTF Futures`
        
    - Bucket: `Oct 2025`
        
    - Value: pulled from ICE daily settlement files
        
2. **Reval Jobs** use the current price to calculate:
    
    - **NPV (MTM)**
        
    - **Unrealized PnL** (vs. prior day’s price)
        
    - **Realized PnL** if variation margin is settled
        

---

### 🧠 Bottom Line

The **monthly granularity** refers to **which period the price applies to**, not **how often the price changes**.

So:

> ✅ **MTM and PnL move every day**, driven by the **daily change in the monthly settlement price** for that contract month.



## ✅ Where to See Daily Price Changes in Endur

### 1. **Market Data Viewer (with History Enabled)**

- Go to **Market Data Viewer** or run the `Rpt_MarketDataHist` report.
    
- Select the **futures market curve** (e.g., `TTF Futures`, `NG Futures`).
    
- Enable the **"Show History"** option or filter by past dates.
    
- This will show:
    
    - Daily settlement prices
        
    - Date-wise curve point values
        
    - You can export to Excel or use for trend analysis
        

> 💡 If this is not visible, ensure your Endur instance is configured to **store historical market data** — it's often configurable via environment settings or `idx_historical_values`.

---

### 2. **`idx_historical_values` Table** (via SQL)

You can directly query Endur’s database to see past values of curve points:

sql

CopyEdit

`SELECT      index_id,     ref_source,     start_date,     end_date,     value FROM      idx_historical_values WHERE      index_id = (SELECT index_id FROM idx_def WHERE index_name = 'TTF Futures')     AND start_date >= '2025-08-01'     AND bucket = 'Oct 2025' ORDER BY start_date;`

> This table holds **historical curve values** if the "store history" flag is enabled when loading market data.

---

### 3. **Saved Snapshots or Market Data Versions**

- If your organization takes **daily market data snapshots** (e.g., for audit or valuation replay), you can:
    
    - Load the curve "as of" a past date
        
    - View the historical price that was active on that day
        

Usually managed by a **curve versioning system** or **snapshot mechanism**.

---

### 4. **Deal Reval Report with Historical Valuation Dates**

If you revalue the futures deal as of different historical dates (e.g., using `Reval` or `SimResult Viewer`):

- You’ll see the NPV, PnL, and price used for each date
    
- This indirectly shows the **price change**, even if the raw market data isn't viewed
    

---

## 🔄 How Daily MTM Movement Happens in Practice

1. Each day’s **settlement prices are imported** into Endur for all active future contract months.
    
2. These **overwrite the prior day’s values** in the market curve.
    
3. Endur calculates **MTM and PnL based on the difference** between today's and yesterday’s prices.
    
4. If you have **historical market data enabled**, this delta can be retrieved and audited.