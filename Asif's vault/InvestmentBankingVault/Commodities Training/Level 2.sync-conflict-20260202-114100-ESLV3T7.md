# **Level 2 – Market Data, Valuation, Risk & Performance**

### _How external reality becomes numbers, controls, and decisions_

## **Level Objective**

Enable participants to understand **how market information enters the organization**, how it is **transformed into prices, PnL, and risk**, and how different stakeholders consume the same numbers for different purposes.

This level explicitly bridges:

- Business reality
    
- Quantitative models
    
- System architecture in **Openlink Endur**
    

---

## **Module 4 – Market Data: Origin, Types & System Modeling**

### _Where all valuation begins_

**Objective**  
Explain what market data is, where it comes from, how it is governed, and how it is modeled and consumed by Endur.

**Scope**

- Types of market data: spot, forwards, indices, fixings, volatility, interest rates, FX
    
- Sources: exchanges, price reporting agencies, brokers, internal marks, models
    
- Market data lifecycle: ingestion → validation → approval → publishing
    
- Governance, controls, and conflicts of interest
    
- Market data objects in Endur: curves, indices, fixings, dependencies
    

**Key Insight**  
Every price, PnL, and risk number is downstream of a market data assumption.

**Outcome**  
Participants understand why market data quality and governance are foundational.

---

## **Module 5 – Pricing, Valuation & PnL Generation**

### _Turning market data into value_

**Objective**  
Explain how pricing models consume market data, how Endur performs valuation at scale, and how PnL is generated over time.

**Scope**

- Pricing vs valuation vs settlement
    
- Pricing models (linear, indexed, optionality – conceptual)
    
- Endur pricing engines and simulation framework
    
- Grids, scenarios, and performance trade-offs
    
- End-of-day processes: revaluation, PnL, risk recalculation
    
- PnL types: unrealized, realized, accruals
    
- PnL explain drivers: market movement, time, trades, data/model changes
    

**Key Insight**  
PnL moves even when no trades occur because models and assumptions evolve.

**Outcome**  
Participants can trace PnL back to market data and pricing logic.

---

## **Module 6 – Risk Factors, Risk Calculations & Stakeholder Views**

### _How uncertainty is observed and controlled_

**Objective**  
Explain how risk is derived from pricing, how it is measured, and how different stakeholders interpret risk.

**Scope**

- Risk factors: price, basis, curve, volatility, volume, credit, liquidity, operational
    
- Risk calculation approaches: position-based, sensitivity-based, scenario-based
    
- Hedging philosophy and residual risk
    
- Stakeholder lenses: trading, risk, finance, credit, operations, management
    
- Risk architecture in Endur: engines, aggregation, limits, breach workflows
    

**Key Insight**  
Risk systems do not predict outcomes — they bound potential damage.

**Outcome**  
Participants understand why risk numbers differ by report and by audience.

---

## **End State of Level 2**

By the end of this level, participants can:

- Explain how market data is created and governed
    
- Understand how pricing models transform data into value
    
- Interpret PnL beyond surface-level numbers
    
- Reason about risk across multiple dimensions
    
- See Endur as an **engine that continuously re-estimates reality**, not a static system