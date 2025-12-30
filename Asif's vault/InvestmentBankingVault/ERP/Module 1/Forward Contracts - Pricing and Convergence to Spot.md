# Forward Contracts: Pricing & Convergence to Spot

## Market Value & Zero-Sum Nature

- **Forward contract value at inception = 0**
    
- As market prices move:
    
    - One side gains → **asset**
        
    - Other side loses → **liability**
        
- Forward contracts are **zero-sum games**:
    
    - Gains of one counterparty = losses of the other
        

### Mark-to-Market (MTM)

- Over contract life, MTM value:
    
    - Fluctuates between positive and negative
        
- Position value depends on:
    
    - Current forward price vs contracted price
        

---

## Long vs Short Positions

### Definitions

- **Long**:
    
    - Benefits from **higher prices**
        
    - Typically must **take delivery and pay**
        
- **Short**:
    
    - Loses from higher prices
        
    - Typically must **deliver commodity**
        

### Important Nuance ⚠️

- Some forwards are **cash-settled** → delivery definition breaks down
    
- **Most general definition**:
    
    - Long = benefits from higher price
        
- In complex structured deals:
    
    - Determining who is long/short may be **non-trivial**
        

---

## Forward & Spot Price Notation

- **Forward price**: `f(t, T)`
    
    - Observed at time `t`
        
    - For delivery/maturity at time `T`
        
- **Spot price**:
    
    - `S(t)` or equivalently `f(t, t)`
        

### Textbook Convergence Rule

- As maturity approaches:
    
    - `f(t, T) → S(T)`
        
- Spot price is treated as:
    
    - Forward with **zero time to maturity**
        

---

## Convergence: Theory vs Reality

### Textbook (Stylised) View

- At maturity:
    
    - Contract expiration
        
    - Financial settlement
        
    - Cashflow event
        
    - **All coincide**
        

### Reality in Energy Markets

- These dates often **do not coincide**
    
- Requires careful handling of:
    
    - Valuation
        
    - Discounting
        
    - Profitability analysis
        

⚠️ **Critical for trading system design (ETRM/Endur)**:

- All relevant dates must be:
    
    - Explicitly captured
        
    - Correctly discounted to valuation date
        

---

## Reversibility of Physical Forwards

- Physical forward ≠ absolute delivery obligation
    
- Positions can be neutralised via:
    
    - Offsetting trades
        
    - **Book-outs** (offsetting trades with same counterparty)
        

---

## Why Convergence Is “Fuzzy”

- Futures/forwards are:
    
    - Precisely defined
        
    - Transparent
        
- Spot prices are often:
    
    - Difficult to observe
        
    - Known only after the fact
        

### Natural Gas Example (CME / Henry Hub)

- Contract size: **10,000 MMBtu**
    
- Expiry: **3 business days before month-end**
    
- Delivery: **Ratable delivery over next calendar month**
    

#### Key Question

> What is the spot price futures should converge to?

Possible references:

1. **Daily gas prices during delivery month**
    
    - Unknown at futures expiry
        
    - Highly weather-dependent
        
2. **Monthly index price (base-load gas)** ✅
    
    - Known on first business day of delivery month
        
    - Fixed price of a **1‑month swap**
        

### Important Insight

- Futures converge to:
    
    - **Expected monthly forward/index price**, not a clean spot price
        
- Even index prices are technically **forwards**
    

---

## Circular Price Formation

- Physical prices influence derivatives
    
- Derivative prices influence physical trades
    

➡️ Prices emerge via a **simultaneous general-equilibrium process**:

> Everything depends on everything else

---

## Practical View on Convergence

- Convergence is a **tendency**, not a guarantee
    
- Imperfect due to:
    
    - Market frictions
        
    - Asynchronous trading
        
    - Imperfect information
        
    - Physical infrastructure limits
        

---

## Why Forward & Futures Markets Dominate

- Spot markets are often:
    
    - Opaque
        
    - Relationship-driven
        
    - Convention-based
        
- Many physical flows are priced using:
    
    - Forward or futures-based formulas
        

➡️ In many energy commodities:

> **A pure spot market does not exist**

---

## Variants of Forward Transactions

### Standard Forward

- Deferred delivery
    
- Deferred payment
    

### Prepaid Forward

- Deferred delivery
    
- **Accelerated payment**
    
- Used by producers to:
    
    - Finance new projects
        

⚠️ Historical misuse:

- Prepays used to **disguise loans** as commodity trades
    

---

# Futures Contracts

## What Makes Futures Different

- Futures = forwards traded on **organised exchanges**
    
- Exchanges provide:
    
    - Standardised contracts
        
    - Trading infrastructure
        
    - Counterparty credit protection
        

### Clearinghouse Role

- Interposed via **novation**
    
- Becomes counterparty to both sides
    
- Guarantees performance
    

---

## Margining System

### Types of Margin

- **Initial margin**
    
    - Performance bond / security deposit
        
- **Maintenance margin**
    
    - Minimum equity threshold
        
- **Variation margin**
    
    - Paid/received due to MTM losses/gains
        

### Example

- Initial margin: $10,000
    
- Maintenance margin: $8,000
    
- Loss of $2,500 → equity = $7,500
    
- Variation margin call = $2,500
    

---

## Futures vs Forwards: Accounting Difference ⚠️

|Aspect|Forwards|Futures|
|---|---|---|
|Settlement|At maturity|Daily (MTM)|
|Cashflows|Future|Immediate|
|Valuation|Discounted NPV|No discounting|
|Liquidity|OTC|Exchange-traded|

- Swaps = portfolios of forwards
    
- Critical structuring risk:
    
    - Treating futures like forwards (or vice versa)
        

⚠️ Many real-world structuring failures stem from this error

---

## Collateralisation in OTC Markets

- Many OTC forwards now:
    
    - Collateralised based on MTM
        
- Possible features:
    
    - Thresholds
        
    - Partial or full collateral waivers
        

---

## Margin Changes & Market Volatility

- Exchanges raise margins after:
    
    - Periods of high volatility
        
- Consequence:
    
    - Forced position liquidations
        
    - **More volatility**, not less
        

### Silver Example

- Margins up **84% in two weeks**
    
- Price drop: **~28% in one week**
    

---

# Forward Price Curve

## Definition

- At time `t`, multiple forward prices exist:
    
    - `f(t, T1), f(t, T2), …`
        
- Entire set = **forward price curve**
    

---

## Curve Frequency Conventions

- Oil & gas: **monthly**
    
- Power markets:
    
    - Hourly → daily → monthly
        
- Some markets use **cascading contracts**
    

### Cascading Example

- Europe (Nordics):
    
    - Annual → quarterly → monthly
        
- US power:
    
    - Summer block → July/August
        

---

## Storing Curves in Systems

### Option 1: Store Original Market Quotes

- Pros: faithful to market
    
- Cons: complex pricing of sub-periods
    

### Option 2: Decompose to Lowest Frequency

- Pros: simpler database, flexible pricing
    
- Cons:
    
    - Loss of original data
        
    - Arbitrary decomposition assumptions
        

---

## Trader Responsibility

- Post end-of-day forward curve
    
- Monitor intraday movements
    
- React to:
    
    - Sudden price changes
        
    - Curve shape shifts
        

### In Illiquid Markets

- Data sources:
    
    - Exchange settlements
        
    - Broker sheets
        
    - Consultant curves
        
- Gaps filled using:
    
    - Trader judgement
        
    - Seasonality assumptions
        

---

## Governance & Risk ⚠️

- Traders can become:
    
    - Sole experts in illiquid niches
        
- Risk:
    
    - Errors
        
    - Intentional misrepresentation
        

➡️ **Middle office responsibility**:

- Validate forward curves
    
- Challenge assumptions
    
- Ensure compliance
    

---

## Key Practitioner Takeaways ⭐

- Convergence is approximate, not exact
    
- Spot prices are often conceptual, not observable
    
- Futures ≠ forwards (accounting & cashflow)
    
- Forward curve construction is:
    
    - Technically hard
        
    - Operationally critical
        
    - A major risk-control point
        

---

## Suggested Obsidian Links

- [[Forward vs Futures Accounting]]
    
- [[Price Convergence in Energy Markets]]
    
- [[Clearinghouses and Margining]]
    
- [[Forward Curve Construction]]
    
- [[Middle Office Curve Validation]]