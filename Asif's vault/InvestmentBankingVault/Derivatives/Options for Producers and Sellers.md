## 🛡️ **1. Hedging Fixed-Price Risk with Options**

### ⚙️ Scenario:

A **producer** fears **falling prices** (e.g., due to warm weather) and wants protection. Current futures price: **$2.15**.

### ✅ Strategy:

Buy a **put option** with a **strike price of $2.15** by paying a premium of **$0.15**.

- A **put option** gives the right (not obligation) to sell futures at $2.15.
    
- Cost of this insurance = $0.15.
    

### 💰 Payout Profile:

- **If futures fall below $2.15**, the put is **"in the money"**. The producer can sell at $2.15, securing a better price.
    
- **Breakeven** = $2.00 (strike price - premium).
    
- **Below $2.00**, producer benefits fully, offsetting the falling market prices.
    
- **Between $2.00 and $2.15** = partial protection but costlier than selling futures outright.
    
- **Above $2.15**, the option expires worthless, but the producer sells at market and just loses the $0.15 premium.
    

### 🧠 Key Insight:

Buying puts is a way to **set a floor price** while retaining upside potential (if prices rise). But it's **not free**—the premium must be accounted for in the effective sale price.

---

## 🛡️ **2. Hedging Fixed-Price Risk for End Users (Buyers)**

### ⚙️ Scenario:

An **end user** fears **rising prices**.

### ✅ Strategy:

Buy a **call option**. This sets a ceiling on what they might have to pay for gas. Similar logic as put options for producers, but flipped.

- Call option = right to buy at a certain strike price.
    
- They pay a premium upfront for this ceiling.
    
- Ensures **maximum purchase price = strike + premium**.
    

---

## 📈 **3. Enhancing Revenues or Lowering Costs Using Options (Covered Options Strategy)**

### 🎭 Background:

- **Producers** are _naturally long_ (they own gas, want to sell).
    
- **End users** are _naturally short_ (they need gas, want to buy).
    
- Both can **sell ("write") options** against their positions to **collect premium**.
    

---

## 💡 Example: End User Sells a Put Option

### ⚙️ Scenario:

An end user needs to buy gas next month and believes prices will rise. So they sell a **$2.15 put option** and **collect $0.15 premium**.

### Payout Profile:

- **Above $2.15** → buyer won’t exercise → end user keeps full premium = $0.15 profit.
    
- **Between $2.15 and $2.00** → put is exercised → end user buys gas at $2.15 (higher than market), but offset with premium.
    
- **Below $2.00** → loss starts adding up, because they are forced to buy at $2.15 even though market is cheaper.
    

### 🧠 Key Insight:

- The end user earns premium **if market stays flat or rises**.
    
- Risk: **They may overpay** for gas if prices fall sharply.
    

---

## 💡 Example: Producer Sells a Covered Call

- Producer sells a call (e.g., strike = $2.15) to collect premium.
    
- If prices rise above strike + premium → **opportunity cost** of not selling at higher price.
    
- If prices fall → option expires, they keep premium but may get lower sale price for gas.
    

---

## 🎯 Key Takeaways:

- **Options give flexibility**: Producers and end users can choose between certainty and flexibility.
    
- **Buying options** protects from price swings, but comes with a cost.
    
- **Selling options** can earn income (premium), but introduces risk and caps benefits.
    
- The trade-offs involve:
    
    - **Protection vs. profit**
        
    - **Cost vs. opportunity**

### 🧾 Producer Use Case:
- **Concern**: Falling natural gas prices.
- **Current Futures Price**: $2.15
- **Strategy**: Buy a **$2.15 put option** for **$0.15**
- **Right**: Sell gas futures at $2.15 regardless of market price.
- **Breakeven**: $2.15 - $0.15 = **$2.00**

#### ⛳ Outcome at Expiration:
- **Below $2.00**: Option exercised → gain = price drop protection.
- **$2.00–$2.15**: Some protection, but costlier than selling futures.
- **Above $2.15**: Option not exercised → effective sale price = market price - $0.15.

> ✅ Puts allow downside protection + upside participation, but at a cost.

---

## 🧾 End User Use Case:
- **Concern**: Rising natural gas prices.
- **Strategy**: Buy a **call option** (right to buy at strike price).
- **Outcome**: 
  - If prices rise → use call, pay strike + premium.
  - If prices fall → option not used, end user buys at market price.

> ✅ Calls set a ceiling price for buyers.

---

## 💸 Enhancing Revenues or Lowering Costs Using Options

### 🎭 Market Positions:
- **Producers** = Naturally **long** (have gas to sell)
- **End Users** = Naturally **short** (need to buy gas)
- Both can **sell covered options** to collect premium.

---

## 🧾 End User Writes (Sells) a Put Option

- **Action**: Sells a $2.15 put, receives $0.15 premium.
- **If price > $2.15**: Option expires worthless → full premium earned.
- **$2.00 < price < $2.15**: Option exercised → must buy at $2.15 (offset by premium).
- **Price < $2.00**: Bigger loss, must buy at $2.15 even though cheaper gas available.

> ⚠️ Risk: Overpaying in a falling market  
> ✅ Reward: Premium offsets cost in stable/rising market

---

## 🧾 Producer Writes (Sells) a Call Option

- **Action**: Sells call option against expected supply.
- **If price > strike + premium**: Loses chance to sell at higher market price.
- **If price < strike**: Keeps premium, sells at market.

> ⚠️ Risk: Opportunity cost of price surge  
> ✅ Reward: Generates income in flat/down markets

---

## 📌 Summary

| Role        | Hedge Tool | Purpose              | Risk                       | Reward                     |
|-------------|------------|----------------------|----------------------------|----------------------------|
| Producer    | Put        | Protect from price drops | Premium cost            | Min. price protection      |
| End User    | Call       | Protect from price rises | Premium cost            | Max. price ceiling         |
| Producer    | Sell Call  | Generate income         | Capped upside             | Premium collected          |
| End User    | Sell Put   | Reduce cost             | May overpay for gas       | Premium collected          |

> 🧠 Options allow participants to **balance price certainty and flexibility** based on their market position and price outlook.



[[Commodity Futures.md]]