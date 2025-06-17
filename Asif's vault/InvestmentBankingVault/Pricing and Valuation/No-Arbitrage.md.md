## 📘 Why Commodity Pricing Models Assume No Arbitrage

### 🔁 What is Arbitrage?

- **Arbitrage** is the risk-free profit made by exploiting price differences across markets or instruments.
    
- Example: Buy oil at $80 in Market A, sell at $82 in Market B → profit = $2 (ignoring costs).
    

---

### 📐 Importance of No-Arbitrage in Pricing Models

Most pricing models **assume no arbitrage** to ensure:

- **Consistency**: Spot, futures, and options prices follow logical relationships.
    
- **Fair Valuation**: Derivatives can be priced using replicable strategies (e.g., cost-of-carry).
    
- **Reliable Risk Management**: Hedging and valuation models depend on stable price linkages.
    

📌 Example: **Cost-of-Carry Model**

	$$
F = S \cdot e^{(r + u - y)t}
$$

- FFF: Futures price
    
- SSS: Spot price
    
- rrr: Risk-free rate
    
- uuu: Storage cost
    
- yyy: Convenience yield
    
- Relies on no-arbitrage to hold true.
    

---

### 🚫 Challenges If Arbitrage Exists

If arbitrage is **persistent** or **not eliminated**, it disrupts:

- ✅ **Model Stability**: Outputs become erratic and untrustworthy.
    
- ✅ **Price Relationships**: Spot-futures and calendar spreads lose structure.
    
- ✅ **Hedging Strategies**: Become inaccurate or ineffective.
    
- ✅ **Risk Pricing**: Volatility surfaces and implied metrics become distorted.
    

---

### ⚠️ Real-World Considerations

While models assume "no arbitrage," in reality:

- Arbitrage opportunities **do occur** but are usually short-lived.
    
- Commodities face **real-world frictions**:
    
    - High transaction or transport costs
        
    - Storage limitations
        
    - Illiquid markets
        
    - Seasonality and political risk
        

---

### ✅ Summary Table

|Assumption|Purpose|
|---|---|
|**No Arbitrage**|Stable, fair, and replicable pricing|
|**Ensures**|Spot, forward, and derivative prices are consistent|
|**Violations cause**|Instability, mispricing, ineffective hedging|