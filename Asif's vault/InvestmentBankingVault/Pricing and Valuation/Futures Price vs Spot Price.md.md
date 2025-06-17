## 🔹 Futures Prices vs Spot Prices — Under No-Arbitrage

### 📌 Why futures prices are linked to spot prices

- Under the **no-arbitrage condition**, prices of the same asset in different markets must move together — otherwise, traders could make **risk-free profits** by exploiting price differences.
    
- If the **spot price of a commodity rises**, traders will act to exploit differences between futures and spot, forcing **futures prices to adjust**.
    
- The **only exception** is when the **risk-free interest rate** changes — because interest rate shifts affect the cost of carrying the commodity over time.
    

---

## 🔹 Should the Futures Price Equal the Expected Spot Price?

### ⚠️ Intuitive but Incorrect Assumption:

- It seems logical to say:  
    `Futures Price = Expected Spot Price at expiry`
    
- But this is **only true** in a **risk-neutral world**, where:
    
    - Everyone agrees on the expected future spot price.
        
    - No one is averse to risk.
        
    - There's no need to adjust for uncertainty.
        

### ✅ Real-World Situation:

- In reality:
    
    - The **path** of spot prices over time is **uncertain**.
        
    - Investors are **risk-averse** and care about **how uncertain** the outcome is.
        
- Hence, the futures price must be adjusted to reflect that uncertainty. This adjustment is called the **risk premium**.
    

---

## 🔹 What Is Risk Premium?

### ➕ Explanation:

- It’s the **difference** between the **futures price** and the **expected future spot price**.
    
- It reflects the **extra compensation** investors require for taking on price uncertainty.
    
- It is not about forecasting — it's about **pricing in risk**.
    

### ✅ When Risk Premium Is Positive:

- Investors demand to be compensated for holding risky assets.
    
- Futures price is set **below** the expected future spot price.
    
- This implies that the **spot price is expected to rise faster** than the risk-free rate.
    

### ❌ When Risk Premium Is Negative:

- Investors **like** the asset because it provides **protection** in bad times (e.g., gold).
    
- They’re willing to accept **lower expected returns** for this "insurance".
    
- Futures price ends up being **above** the expected future spot price.
    

---

## 🔹 What Is Net Convenience Yield?

### 🧰 Explanation:

- It’s the **benefit** of physically holding the commodity rather than owning a paper claim (futures).
    
- For example, a utility might **prefer to store physical gas** for guaranteed supply rather than rely on a futures contract.
    

### 🔄 Relationship:

- A higher convenience yield means the spot asset is **more valuable** than the futures contract.
    
- The futures price gets **discounted** relative to the spot price.
    

Formula context:

java

CopyEdit

`Futures Price = Spot Price + Cost of Carry - Convenience Yield`

---

## 🔹 Investors’ Preferences and Asset Correlation with Income

### 🧠 Investor Behavior:

- Investors **prefer assets** that **increase in value during bad times**, when their income is low (negative correlation with income).
    
- These assets act as **hedges** or **insurance**.
    

### ⚠️ Problem with Many Commodities:

- Many risky assets (like oil) are **positively correlated with income**:
    
    - During economic booms: both incomes and commodity prices rise.
        
    - During recessions: both fall.
        
- This makes them **poor hedges** — they don't protect income during downturns.
    
- Investors demand a **positive risk premium** to hold such assets, pushing **futures prices below expected spot**.
    

---

## 🔚 Conclusion (Still Explanation-Oriented)

- Futures prices are **not pure forecasts** of spot prices.
    
- They are shaped by:
    
    - Arbitrage relationships.
        
    - **Risk aversion and uncertainty** → risk premium.
        
    - **Physical benefits** of holding the asset → convenience yield.
        
    - **Correlation with macroeconomic variables** like income.
        
- Futures pricing reflects a **risk-adjusted view of the future**, not a naïve expectation of spot price.