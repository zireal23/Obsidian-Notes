# Speculative Swing Swap Strategies – Obsidian Notes

## 1. Nature of Speculative Swing Swap Trading

Speculators use **swing swaps** to gain price exposure to the physical natural gas market **without handling physical delivery**. A swing swap is a financial instrument that settles on the difference between a **fixed price** and the **floating daily index average** for the month.

The most common speculative applications are:

- **Outright Directional Bets**: Buy swing swaps expecting prices to rise, or sell expecting them to fall.
    
- **Spread Trading (Convergence/Divergence)**: Pair a swing swap position with an opposite futures position.
    

In convergence trades, traders:

- Buy a swing swap (long exposure to cash/index prices)
    
- Sell short a nearby futures contract (short exposure to futures)
    
- Profit if the index price rises and the futures price falls (prices converge).
    

---

## 2. Are Physical Volumes Traded in Speculative Strategies?

No. Despite referencing physical markets:

- **Swing swaps** are **financial instruments**.
    
- **Futures contracts** are also **cash-settled** if closed before expiration.
    

Therefore:

- You **do not buy or sell real gas**.
    
- You **do not need to find a counterparty to deliver/receive gas**.
    
- You're simply exposed to price differences and settle in cash.
    

Your volume is **notional** – it just determines the scale of your PnL calculation.

---

## 3. Formula for PnL in Convergence Trade

Assuming:

- `P_fixed_swing` = Fixed price in swing swap
    
- `P_index_avg` = Floating monthly index average (daily average index price)
    
- `P_futures_entry` = Price you shorted the futures contract
    
- `P_futures_exit` = Price you bought back the futures
    

### Net PnL per unit:

```
(P_index_avg - P_fixed_swing) + (P_futures_entry - P_futures_exit)
```

This reflects:

- Gain/loss on swing swap leg
    
- Gain/loss on futures leg
    

> 📌 Remember: No physical cash is exchanged beyond the net financial result.

---

## 4. Real-World Conditions Where Index Rises & Futures Fall

This scenario benefits convergence trades where you:

- Buy swing swap (gain if index rises)
    
- Short futures (gain if futures fall)
    

### Scenarios:

|Scenario|Index (Cash)|Futures|Explanation|
|---|---|---|---|
|Pipeline failure|↑|↓|Spot market panic vs long-term calm|
|Extreme weather|↑|↓|Short-term spike, long-term unchanged|
|Storage injection season|↑|↓|Temporary demand vs supply surplus|
|Macro bearish supply news|↑|↓|Spot market tightness vs bearish outlook|
|End-of-month delivery pressure|↑|↓ or ↔|Cash price spikes after futures expiry|

### Key Insight:

Index prices respond to **short-term delivery urgency**, while futures reflect **longer-term expectations**. This mismatch can be exploited.

---

## 5. Additional Notes

- Managing the futures leg in convergence trades requires **daily adjustments** since the swing swap's floating leg accumulates daily index prices.
    
- Futures expire before month-end, so the last 5–6 days leave you exposed to only the swing swap leg.
    
- Weekends may require liquidation of futures in **larger chunks** (e.g., 3 days’ worth on Friday).
    

---

## Summary

- Swing swaps are cash-settled instruments referencing monthly average physical gas prices.
    
- Futures are traded alongside them to construct convergence/divergence spreads.
    
- You are not physically trading gas — it's all **financial speculation** on relative price movement.
    
- Net PnL depends on how cash index and futures prices move **relative to each other**, not in absolute terms.
    
- Certain real-world events and market structures can create profitable convergence opportunities.
    

---

> ✍️ Consider simulating daily price movements and managing futures position daily to better understand the cash flow evolution of this strategy.

---

Tags: #commodities #natural_gas #swing_swaps #futures #spread_trading #convergence #trading_strategies

[[Swing Swaps.md]]