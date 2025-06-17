## 🧾 Hedging a Swing Swap (Buy or Sell) Using Physical Gas

### 📌 What is a Swing Swap?

A **swing swap** is a **financial derivative** contract that allows market participants to gain or hedge **exposure to daily gas price fluctuations** at a specific location (e.g., Permian).

- It is **cash-settled**, not physically delivered.
    
- Pricing is based on the **average of daily index prices** during the contract period (typically monthly).
    
- Traders use swing swaps to **speculate on or hedge against daily price volatility**.
    

---

## 🎯 Hedging Objective

When a trader **cannot offset a swing swap** with another swap (e.g., due to liquidity issues or lack of counterparties), the **hedging strategy shifts to the physical market**.

> 💡 **Goal**: Neutralize exposure to floating daily index by transacting in the **physical gas market**, while **locking in a fixed margin**.

---

## 📘 Hedging a **Swing Swap Sale**

### 🧩 Trade Setup

- You **sell** a **January Permian swing swap** at **$2.00/MMBtu**.
    
- You can **buy fixed-price baseload gas** at **$1.95/MMBtu**.
    

|Element|Value|
|---|---|
|Swing Swap Sale|+ $2.00 / MMBtu|
|Physical Baseload Purchase|– $1.95 / MMBtu|
|**Margin So Far**|= $0.05 / MMBtu|

🟡 But: You are still **long physical gas**. You must now sell this gas daily to recover the floating side of the swap.

---

### 🔄 Hedge Execution (Day-to-Day)

- Sell baseload gas **daily** into the **physical spot market** at the **daily index**.
    
- The swing swap **requires you to pay the daily index**, so you want to recover that by selling physical at the same price.
    

|Cash Flow Component|Explanation|
|---|---|
|**Pay Permian supplier**|– $1.95 fixed (baseload contract)|
|**Receive from swing swap**|+ $2.00 fixed|
|**Pay to swing swap (index)**|– avg(Jan Permian daily index)|
|**Receive from physical sale**|+ avg(Jan Permian daily index)|
|**Net Profit**|= $0.05 / MMBtu|

✅ If you're able to sell physical gas each day **at the daily index**, the floating legs cancel out.

---

### 📊 Diagram – Cash Flows

pgsql

CopyEdit

            `+---------------------------+             |   Sell Swing Swap @ $2.00 |             +---------------------------+                       ↑        ↓         +-------------+        +---------------------+         | Pay Daily Index       |                     |         | to Customer           |                     |         +----------+            ↓                     ↓                    |     Sell Physical Gas     Buy Baseload Gas                    |     at Daily Index        @ $1.95 Fixed                    ↓            ↑                    ↑         +----------+------------+--------------------+         | Net = $2.00 - $1.95 = $0.05 / MMBtu Profit |         +--------------------------------------------+`

---

## 📘 Hedging a **Swing Swap Purchase**

### 🧩 Trade Setup

- You **buy** a **swing swap** at **$2.00/MMBtu**.
    
- You can **sell baseload physical gas** at **$2.05/MMBtu**.
    

> Now, you're **short the index** and must purchase daily physical gas to fulfill your fixed physical sale.

---

### 🔄 Hedge Execution (Day-to-Day)

- Buy physical gas **daily at the index**.
    
- You're receiving a **fixed sale price** of $2.05.
    
- The swing swap **reimburses you** at $2.00.
    
- If you buy physical gas daily **at or below the daily index**, the index exposures cancel.
    

|Cash Flow Component|Explanation|
|---|---|
|**Receive from physical sale**|+ $2.05 fixed (baseload sale)|
|**Pay for swing swap**|– $2.00 fixed|
|**Buy physical gas daily**|– avg(Jan daily index)|
|**Receive from swing swap**|+ avg(Jan daily index)|
|**Net Profit**|= $0.05 / MMBtu|

✅ Once again, index exposures cancel, and you retain the **fixed margin**.

---

## 🧱 Why Use Baseload Contracts?

|Contract Type|Characteristics|Use in Swing Swap Hedging|
|---|---|---|
|**Baseload**|Fixed price, best-effort volume delivery, typically used for consistent delivery throughout the month|✅ Ideal — gives price certainty|
|**Swing**|Price indexed to daily spot, variable volume; often unreliable performance|❌ Avoid — introduces uncertainty|
|**Firm**|Guaranteed volume and performance, but more expensive or inflexible|⚠️ Possible, but not ideal|

> ⚠️ Baseload contracts strike the **best balance** between price certainty and operational flexibility when hedging financial products like swing swaps.

---

## 🔍 Risk Considerations

|Risk Type|Description|
|---|---|
|**Execution Risk**|Inability to buy/sell daily physical gas at the daily index price can erode or eliminate profit.|
|**Volume Risk**|Baseload contracts are best-effort, not guaranteed. You may fall short of supply/demand on a given day.|
|**Liquidity Risk**|Daily gas markets may not be deep enough for the trader to transact at index on high volatility days.|
|**Credit Risk**|Counterparty failure in either swing swap or baseload deal can disrupt the hedge.|

---

## ❓ FAQs

### Q: Why not use a swing contract to hedge a swing swap?

> Because swing contracts are unreliable in daily delivery and are themselves **indexed to the daily price**—they don’t solve your problem of **locking in a fixed cost**.

---

### Q: What makes a baseload contract ideal?

> A baseload contract allows you to **lock in a fixed monthly price** without the performance rigidity of a firm contract. It's also **more liquid and flexible** than firm supply.

---

### Q: What happens if daily gas trades below index?

> You gain additional profit. You still charge or pay the daily index on the swap leg, but pay less or sell higher in the physical market.

---

### Q: What if I can't sell or buy at index levels every day?

> Your index exposure is unhedged, and your **margin is at risk**. The entire trade becomes speculative and could generate a loss.

---

## ✅ Summary

| Element                | Detail                                               |
| ---------------------- | ---------------------------------------------------- |
| **Instrument Hedged**  | Swing Swap (Buy/Sell)                                |
| **Hedging Tool**       | Baseload Physical Gas Contract                       |
| **Floating Exposure**  | Daily Index (Price Volatility)                       |
| **How It’s Hedged**    | Daily sales or purchases in physical market at index |
| **Margin Capture**     | Fixed-price spread (swing vs. baseload)              |
| **Key Success Factor** | Transacting daily at/near index in physical market   |
[[Swing Swaps.md]]