## 📘 Trigger Deals in Natural Gas Markets

---

### 🔹 Overview: What Is a Trigger?

A **Trigger** is a hybrid pricing structure in the natural gas market that allows one party (typically the buyer) to **lock in a fixed price** for physical gas **at a later date**.

It consists of:

- A **basis swap**
    
- An **index-priced physical gas deal**
    
- A **futures swap** added later when the buyer "triggers" (i.e., elects to fix the price)
    

Unlike an EFP (Exchange for Physical), where both physical and futures legs are executed simultaneously, a trigger **postpones the futures leg** — giving the buyer control over when to fix the price.

---

## 🧩 Components of a Trigger

|Component|Description|
|---|---|
|**Index Gas**|Physical gas bought/sold at a floating market index (e.g., Chicago Index)|
|**Basis Swap**|Adjusts price from Henry Hub to physical location (e.g., Chicago)|
|**Futures Swap**|Added upon trigger to fix the Henry Hub price|

At initiation:

- You have a **basis swap** and **index gas**
    
- After triggering:
    
    - You **add a futures swap**
        
    - Result = **Fixed-price gas**
        

---

## 🕒 Trigger Timing

- Buyer can **choose when to trigger**, i.e., when to execute the futures swap
    
- Trigger deadlines vary:
    
    - Earliest: any time prior to 3rd-to-last trading day
        
    - Latest: ~30 minutes before futures contract expiry
        
- If the buyer **does not trigger** by the deadline:
    
    - The price defaults to **L3D (last 3rd day settle)** ± agreed basis differential
        

---

## 🔁 Hedging a Trigger

|Position Held|Hedging Strategy|
|---|---|
|**Long trigger** (buy)|Short basis swap or short index gas|
|**Short trigger** (sell)|Long basis swap or long index gas|

Triggers are often hedged **like EFPs**:

- Index gas → Hedged via fixed-for-index swap
    
- Basis exposure → Hedged via basis swap
    
- Futures exposure → Via standard futures positions
    

---

## 🧮 Pricing Mechanics: How the Futures Leg Fixes the Price

### Without Triggering:

> Buyer pays = **Floating Index Price + Basis**

### After Triggering:

Buyer enters a **futures swap**:

> Sell Henry Hub futures at a fixed price (e.g., $2.90)

#### Numerical Example:

|Market Inputs|Value|
|---|---|
|Chicago Index|$2.88|
|Basis Swap|+$0.10|
|Henry Hub Futures Sold|$2.90|
|Henry Hub Settle|$2.78|
|Futures Gain|+$0.12|

**Net Effective Price =**

> $2.88 (index) + $0.10 (basis) – $0.12 (futures gain) = **$2.86**

Result: **Price is fixed in advance**, regardless of future index volatility.

---

## 📐 Alternate Perspective: Trigger as a Synthetic Fixed-Price Position

### ✅ Key Insight:

> A **futures swap + basis swap** = a **fixed-for-index swap** for a specific location  
> When added to a **long index gas** position → The index cancels out  
> → Net result: **Fixed-price gas**

---

### 🧠 Step-by-Step Breakdown

#### 1. **Futures Swap (at Henry Hub)**

- You **sell futures** at $2.90
    
- Cash flow: Receive floating (index), Pay fixed
    

#### 2. **Basis Swap**

- You **buy basis** (e.g., +$0.10 Chicago-Henry Hub)
    
- Cash flow: Receive Chicago Index, Pay Henry Hub Index
    

#### ➕ Combine Futures + Basis Swap:

> Receive: Chicago Index  
> Pay: Fixed  
> → This = **Fixed-for-Chicago Index swap**

#### 3. **Add Physical Index Gas**

- You **buy gas at Chicago Index**
    
- So you pay index → cancels with received index from swap
    

---

### ✅ Final Position:

|Leg|Cash Flow|
|---|---|
|Fixed-for-Index Swap|Pay fixed, get index|
|Index Gas Purchase|Pay index|
|🔄 Net|**Pay fixed**|

> 🎯 Result: You’ve synthetically **converted index gas into fixed-price gas**

---

## 🎯 Why Use Triggers?

- Customers (e.g., utilities, industrials) **may not have futures accounts**
    
- Triggers give **price flexibility** — fix the price when market conditions are favorable
    
- Traders provide the infrastructure, and **profit** by:
    
    - Charging wider **basis differentials**
        
    - **Scalping** on the futures swap price
        
    - Charging for **administrative handling**
        

---

## ⚖️ Triggers vs EFPs vs Separate Swaps

|Feature|Trigger|EFP|Separate Swaps|
|---|---|---|---|
|Futures Account|Not required for customer|Required for both parties|Required for swaps|
|Timing|Futures leg added later|Both legs executed simultaneously|Executed independently|
|Admin Burden|High (trader must manage trigger)|Moderate|Moderate to High|
|Flexibility|High|Low|High (but operationally heavier)|

---

## 🧠 Key Takeaways

- Triggers are **flexible EFP-style structures** allowing a party to **fix a physical gas price** later
    
- They consist of:
    
    - Index gas
        
    - Basis swap
        
    - Futures swap (added upon trigger)
        
- When fully triggered, a trigger position is **economically identical** to a **fixed-price physical gas trade**
    
- From a synthetic standpoint:
    
    > **(Fixed-for-index swap) + (Index gas) = Fixed-price gas**
    
    [[Exchange of futures for physical gas]]
    [[Basis Swaps.md]]
    [[Exchange futures for physical- Key points]]
	 [[Forward and Futures Contracts.md]]