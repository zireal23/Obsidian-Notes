## 📘 Hedging a Trigger Sale with an EFP – Full Trade Walkthrough (FJS Case Study)

### 🧩 Trade Overview

- **Customer Request:** Wants a _trigger sale_ on Permian gas (priced off futures), but has **no futures account**.
    
- **FJS Solution:**
    
    - Sells the customer a **trigger** (price based on futures).
        
    - Hedges this exposure by **buying a Permian EFP** (physically settled) and later **selling a futures swap** when the customer triggers.
        

---

### 🛠️ Step-by-Step Mechanics

---

### 1️⃣ EFP Transaction

- FJS **buys a Permian EFP** at **–$0.27** differential.
    
- This means:
    
    - **FJS receives physical gas** in Permian.
        
    - **Transfers out a futures contract** → now **short 1 futures contract at L3D**.
        
- EFP price mechanics:
    
    - Pay: `Posted Price – $0.27`
        
    - Receive: Futures contract at Posted Price
        

#### ✅ Net Result from EFP:

- Physical position = **+1 Permian contract**
    
- Futures position = **–1 contract (short)**
    
- Cash flow = **+$0.27 profit on paper**
    

---

### 2️⃣ Selling Trigger to Customer

- FJS **offers a Permian trigger** at **–$0.25** basis.
    
- Customer agrees to **trigger by L3D–4 (4th last futures trading day)**.
    
- This locks FJS into providing gas at **Posted Price – $0.25** when the customer triggers.
    

#### ✅ Margin Locked:

- EFP was bought at –$0.27
    
- Trigger sold at –$0.25
    
- **Profit: $0.02 per contract**
    

---

### 3️⃣ Customer Triggers

- Customer sees futures trading **$2.25** and calls to trigger.
    
- FJS checks market: bid/ask = **$2.24/$2.25**
    
- Quotes **$2.255** as the fixed price on futures swap (adds a $0.005 spread).
    

### Futures Swap Mechanics:

- FJS **sells a futures swap**:
    
    - **Receives floating (futures)** from customer.
        
    - **Pays fixed $2.255** to customer.
        
- FJS **hedges by buying 1 futures contract at $2.245**.
    

#### ✅ Net Swap Result:

- Fixed sold = $2.255
    
- Futures bought = $2.245
    
- **Profit = $0.01 per contract**
    

---

### 🧮 Total Cash Flow Summary (per contract)

|Flow Component|Amount|
|---|---|
|**EFP**: Receive P, pay P – 0.27|**+0.27**|
|**Trigger sale**: Deliver gas at P – 0.25|**–0.25**|
|**Futures swap spread**: $2.255 – $2.245|**+0.01**|
|**Total Net Profit**|**✔️ +$0.03 per contract**|

---

### 🧠 Key Insights

- **FJS is not double-short futures.**
    
    - The EFP makes them short 1 futures contract.
        
    - The futures swap requires them to be **long floating**, so they **buy 1 futures contract**, neutralizing the position.
        
- **Trigger + EFP = a synthetic fixed-price physical deal.**
    
    - Once the customer triggers, FJS wraps up the trade like a regular fixed-price sale.
        
    - No need for separate swap accounting past trigger.
        
- **FJS earns profit by:**
    
    1. Tightening the trigger basis (–$0.27 → –$0.25 = **$0.02** gain)
        
    2. Pricing swap with a slight markup (**$0.01** gain)
        

---

### 🏁 Final Position Recap

|Position Type|Net|
|---|---|
|**Futures exposure**|Flat (–1 from EFP, +1 from hedge)|
|**Physical position**|Flat (Received in EFP, delivered to customer)|
|**Cash profit**|✅ **+$0.03 per contract**|

![[Pasted image 20250612110754.png]]

[[Triggers]]
[[Exchange futures for physical- Key points]]
[[Exchange of futures for physical gas]]