## 📘 Hedging a Trigger Sale with Fixed-Price Physical Gas

### 🔍 Context

A **trigger sale** allows a customer to price a physical gas deal by "triggering" a futures price at a later date.  
This is often used by customers **without a futures account**, but who still want to price physical gas based on futures.

### 🎯 Objective

FJS (a trading firm) has:

- A **Permian trigger sale** at **futures minus $0.25**
    
- The goal is to **hedge this exposure** using physical gas and swaps (not using EFP)
    

---

## 🧩 Trade Breakdown and Risk Exposure

### Step 1: Initial Exposure

- Trigger sale price = **futures - $0.25**
    
- Risk: **Basis Risk** (Permian vs Futures)
    
- No fixed-price physical gas yet bought.
    

### Step 2: Hedge Basis Risk

- Buy **Permian basis swap** at **L3D - $0.27**
    
- Result: FJS is now long basis at -$0.27 while short to customer at -$0.25
    
- ✅ Locks in a **+$0.02** profit on basis
    

### ➕ New Position Equivalent

Now the effective price FJS is offering becomes:  
**Index + $0.02**

---

## 🛠️ Next Step: Buy Physical Gas to Lock in Fixed Price

### Market Options:

1. **Fixed Float Index Swap Bid** = $2.00
    
2. **Create Synthetic Index Swap:**
    
    - Futures bid = $2.26
        
    - Basis bid = L3D - $0.25
        
    - Result = $2.26 - $0.25 = **$2.01**
        

### Trading Strategy

- Aim to **buy physical gas at $2.00**
    
- Sell futures at $2.26
    
- Sell basis swap at L3D - $0.25
    
- Better by $0.01 than the outright index swap
    

---

## 🔒 Final Hedged Position (Assumptions):

- FJS **pays $2.00** for physical Permian gas
    
- Sells:
    
    - **Basis swap at L3D - $0.25**
        
    - **Futures at $2.26**
        
- Customer triggers at **$2.255**
    

FJS then **buys back futures at $2.245** to close out the position.

---

## 📊 Payment and Receipt Schedule

|Flow|Type|Amount|
|---|---|---|
|Gas Sale to Trigger Customer|Receive|L3D – $0.25|
|Pay to Basis Swap (Customer)|Pay|L3D – $0.27|
|Receive from Basis Swap (Market)|Receive|Index|
|Pay to Physical Supplier|Pay|$2.00|
|Sell Futures|Receive|$2.26|
|Receive from Basis Swap (Market)|Receive|L3D – $0.26|
|Pay to Basis Swap (Customer)|Pay|Index|
|Pay to Close Futures Short|Pay|$2.245|
|Receive from Futures Swap (Customer)|Receive|$2.255|

---

## 💰 Total Profit Calculation

### Futures PnL:

- Sold futures = $2.26
    
- Bought back = $2.245  
    → **Profit = $0.015**
    

### Basis PnL:

- Short to customer at -$0.25
    
- Bought at -$0.27  
    → **Profit = $0.02**
    

### Physical Gas Arbitrage:

- Target = $2.00
    
- Index + Basis + Futures combo = $2.01  
    → **Extra Profit = $0.01** (if executed optimally)
    

### 📈 Total Profit

**$0.015 (futures) + $0.02 (basis) + $0.01 (index arbitrage) = $0.043** per MMBtu  
👉 **Total Profit = $0.043 × number of contracts**

---

## 💡 Key Learnings

- Triggers allow customers without futures accounts to still participate in futures-indexed pricing.
    
- If an **EFP** (Exchange for Physical) is not available, hedging must be done **in steps**:  
    First, hedge **basis**, then hedge **fixed price** via **physical + swaps**.
    
- There is often **pricing inefficiency** between the **outright index swap** vs. a **synthetic combo** of futures and basis—profitable if executed correctly.
    
- **Buying physical at fixed price** and **selling paper (futures + basis)** provides hedging flexibility and potential upside.
    
- Triggers represent both **hedging complexity** and **profit opportunity** for traders with market access.
![[Pasted image 20250613105702.png]]

[[Hedging Triggers with EFP]]
[[Triggers]]
[[Basis Swaps.md]]
