## 🆚 Swing Swaps vs. Vanilla Fixed-for-Floating Swaps

|Feature|**Swing Swaps**|**Vanilla Fixed-for-Floating Swaps**|
|---|---|---|
|**Settlement Frequency**|**Daily** (settles against each day's index)|**Monthly** (settles against the **average** monthly index)|
|**Volume Flexibility**|Often tied to **variable daily volume** or optionality|Fixed monthly volume (typically no swing optionality)|
|**Use Case**|Used to hedge **daily volatility**|Used to hedge **monthly average price exposure**|
|**Underlying Index**|**Daily price index** (e.g., Gas Daily)|**Monthly price index** (e.g., Inside FERC, Platts MTD avg)|
|**Physical Hedge Compatibility**|Aligns with **daily physical trading** activities|Aligns with **monthly baseload or term contracts**|
|**Granularity of Hedge**|High granularity—tracks daily fluctuations|Low granularity—smooths volatility over the month|
|**Speculative Utility**|Can be used to **speculate on day-to-day price swings**|Speculates on broader **monthly trend**|
|**Hedging Operational Gas Risk**|Good fit for ops that nominate daily (e.g. swing load)|Suitable for flat baseload demand|
|**Price Risk Exposure**|Exposed to **daily price swings**|Exposed to **monthly average price**|
|**Common Counterparties**|Traders with daily market exposure|Utilities, industrials, marketers with monthly demand|

---

## 🧠 So Why Use Swing Swaps Over Vanilla Fixed-Float Swaps?

### ✅ 1. **Daily Price Exposure Coverage**

- If you're buying/selling physical gas in the **day market** (e.g., gas is priced daily at index), then swing swaps **mirror your risk**.
    
- Vanilla fixed-float swaps don’t protect you against **volatile daily movements**, only the **average of the month**.
    

### ✅ 2. **Better Hedge for Variable Demand / Load**

- Swing swaps are well-suited to **load-following supply** (like gas-fired power plants or city gate deliveries) where **volume and price fluctuate daily**.
    
- Vanilla swaps assume **constant volumes** and **monthly pricing**, making them **mismatched for operations** with real-world variability.
    

### ✅ 3. **Speculative Edge on Daily Volatility**

- If you believe the **average of daily indexes** will diverge from the **monthly index**, or you're betting on **daily volatility**, swing swaps give you more room to profit or manage risk.
    
- Vanilla swaps are less sensitive to daily price patterns.
    

### ✅ 4. **Alignment with Daily Cashflows**

- Physical gas is often invoiced based on **daily indexes** (e.g., Gas Daily Permian Index).
    
- Swing swaps **cash-settle against the same benchmarks**, making your P&L and hedging clean and traceable.
    

---

## 🧾 Example: Trader Selling Physical Gas at Daily Index

|Use Case|Best Instrument|
|---|---|
|Selling physical gas daily at index, want to fix price|**Sell a Swing Swap**|
|Selling monthly baseload gas, want to lock average index|**Sell a Fixed-Float Swap**|

---

## 🔄 Summary

| Want to Hedge Against…                                    | Use…                       |
| --------------------------------------------------------- | -------------------------- |
| Daily index fluctuations (physical or financial exposure) | ✅ **Swing Swap**           |
| Monthly index average (e.g. term contracts)               | ✅ **Fixed-for-Float Swap** |
| Optional or variable daily volumes                        | ✅ **Swing Swap**           |
| Flat, committed baseload volumes                          | ✅ **Fixed-for-Float Swap** |

---

## ⚠️ Caution

- Swing swaps are **more complex operationally** due to daily settlements.
    
- Managing physical hedge positions with swing swaps requires strong **daily scheduling and gas control**.