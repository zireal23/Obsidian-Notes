# 🔥 Natural Gas (NG) — Practical Learning Curriculum

## 🎯 Goal
Develop **trader-level fluency** in Natural Gas:
- Understand physical flows
- Speak to traders & middle office
- Understand pricing, risk, and arbitrage
- Map everything to Endur (ETRM systems)

---

## 🧭 Module 0 — Big Picture

> Natural Gas = regional, infrastructure-constrained, seasonal commodity with storage optionality

Key characteristics:
- Cannot be transported freely (pipeline constraints)
- Strong seasonal demand (weather-driven)
- Storage creates arbitrage opportunities

---

## 🌍 Module 1 — Physical Reality of Natural Gas

### 1.1 Production (Upstream)
- Conventional gas vs shale gas
- Associated gas (produced with oil)
- Production basins (e.g., Permian, Marcellus)

**Key Insight:**
- Production is not instantly flexible → supply shocks matter

---

### 1.2 Processing
- Removal of impurities:
  - Water
  - CO₂
  - Sulfur
- Output: pipeline-quality gas

---

### 1.3 Transportation (Midstream)
- Pipelines are the core infrastructure
- Compressor stations maintain pressure

**Key Insight:**
> Gas flows through a constrained network, not freely like oil

---

### 1.4 Storage
- Underground storage:
  - Salt caverns
  - Depleted reservoirs

- Two operations:
  - Injection (summer)
  - Withdrawal (winter)

**Key Insight:**
> Storage is central to trading and arbitrage

---

### 1.5 Consumption (Downstream)
- Power generation (largest demand driver)
- Industrial consumption
- Residential heating

---

## ❄️ Module 2 — Seasonality & Demand

### Seasonal Pattern:
- Summer → low demand → injection season
- Winter → high demand → withdrawal season

### Key Drivers:
- Weather (primary driver)
- Power demand (cooling vs heating)
- LNG exports

**Core Idea:**
> Natural Gas behaves like a weather-driven commodity

---

## ⚙️ Module 3 — Market Structure & Pricing

### 3.1 Hubs & Benchmarks
- Henry Hub (primary US benchmark)
- Regional hubs → pricing differences

---

### 3.2 Pricing Structure
- Spot prices
- Forward curves

#### Contango vs Backwardation
- Storage economics depend on curve shape

**Example:**
- Summer price = $2
- Winter price = $4
→ Storage arbitrage opportunity

---

### 3.3 Basis Pricing

> Price = Benchmark + Location differential

Reasons:
- Pipeline constraints
- Regional supply-demand imbalance

---

## 🔄 Module 4 — Trading Mechanics

### 4.1 Physical Trading
- Buying/selling gas at hubs
- Managing delivery obligations

---

### 4.2 Financial Trading
- Futures (Henry Hub)
- Swaps (fixed vs floating)
- Options

---

### 4.3 Core Trade Types

#### 1. Location Arbitrage (Basis Trade)
- Buy in cheaper region
- Sell in expensive region

#### 2. Time Arbitrage (Storage Trade)
- Buy in summer
- Sell in winter

#### 3. Flow Trading
- Optimize pipeline capacity usage

---

## ⚖️ Module 5 — Hedging & Risk

### 5.1 Why Hedge?
- High price volatility (weather-driven)
- Physical exposure to price movements

---

### 5.2 Hedging Instruments
- Futures
- Swaps
- Options

---

### 5.3 Risk Types

#### Price Risk
- Movement in benchmark (e.g., Henry Hub)

#### Basis Risk
- Changes in regional price spreads

#### Volume Risk
- Uncertain demand

#### Operational Risk
- Pipeline outages
- Storage constraints/failures

---

## 🧠 Module 6 — Arbitrage

### 6.1 Storage Arbitrage
- Profit = Winter price – Summer price

Depends on:
- Storage cost
- Injection/withdrawal limits

---

### 6.2 Pipeline Arbitrage
- Exploit regional price differences due to constraints

---

### 6.3 LNG Arbitrage
- Ship gas globally when spreads are favorable

---

## 🏦 Module 7 — Why Banks Trade Natural Gas

### 7.1 Client Flow
- Producers hedge production
- Utilities hedge consumption

→ Bank acts as intermediary

---

### 7.2 Market Making
- Provide liquidity in swaps/options

---

### 7.3 Structured / Proprietary Trading
- Storage optimization
- Spread trading

---

### 7.4 Risk Warehousing
- Temporarily hold client risk

---

## 💻 Module 8 — Mapping to Endur (ETRM Systems)

### 8.1 Core Deal Types
- Physical gas deals (daily/monthly)
- Swaps (fixed vs floating)
- Storage contracts
- Transport contracts

---

### 8.2 Key Dimensions

| Dimension | Example |
|----------|--------|
| Location | Henry Hub |
| Time | Daily / Monthly |
| Volume | MMBtu |
| Price | Fixed / Floating |

---

### 8.3 Example — Storage Trade

#### Physical World:
- Buy gas in summer
- Store gas
- Sell gas in winter

#### Endur Representation:
- Deal 1: Buy (summer forward)
- Deal 2: Storage contract
- Deal 3: Sell (winter forward)

---

### 8.4 Risk in Endur
- Mark-to-market (MTM)
- PnL tracking
- Exposure by:
  - Time
  - Location

---

## 📚 Resources

### Primary
- Natural Gas Trading — Fletcher Sturm

### Supporting
- CME Group (Henry Hub futures)
- EIA (storage reports, market data)

---

## 🧩 Learning Method (VERY IMPORTANT)

For every topic:

### Step 1 — Understand Physical Reality
- What is happening in real life?

### Step 2 — Identify Constraints
- Where are the bottlenecks?

### Step 3 — Find Profit Opportunities
- How can traders make money?

### Step 4 — Translate to Endur
- What would the deal look like?
- What parameters are needed?

---