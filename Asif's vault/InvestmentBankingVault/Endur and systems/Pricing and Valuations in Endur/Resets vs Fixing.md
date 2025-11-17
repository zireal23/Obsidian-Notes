## 🩶 Are **Fixings and Resets the same in Endur?**

### ✅ They are **closely related but not exactly the same**:

---

### 1️⃣ **Fixing (Price Fixing)**

- Refers to the **act of determining and recording the price of an index for a given date.**
    
- It is **market data** captured and stored in **`index_historical_prices`.**
    

**Example:**

- On 2025-07-31, Platts publishes the August 2025 Bidweek gas index price = 3.50.
    
- This fixing is loaded into `index_historical_prices`:
    
    ini
    
    CopyEdit
    
    `start_date = 2025-07-31 reset_date = 2025-08-01, 2025-08-02, ... (each applicable date) price = 3.50`
    

---

### 2️⃣ **Reset**

- Refers to **the process in Endur where a deal fetches the relevant fixing and applies it to determine cashflows, MTM, and settlement amounts.**
    
- Resets occur in the **deal’s Reset Tab** and are tracked individually for **each delivery/pricing period**.
    

---

## ✅ Relationship:

> **“A reset uses a fixing.”**

✅ The **fixing is the price data.**  
✅ The **reset is the deal-level process of applying that price to calculate payments and valuations.**

---

## 🩶 Simple Analogy:

- **Fixing = publishing and recording the index price.**
    
- **Reset = using that price in your deal to calculate what you pay or receive.**
    

---

## ✅ Example:

### **Fixing:**

- Platts publishes:
    
    yaml
    
    CopyEdit
    
    `Date: 2025-07-31 Index: Platts GD Price: 3.50`
    
- Loaded into `index_historical_prices`.
    

---

### **Reset:**

- Your **daily physical gas deal for 2025-08-15** requires a price.
    
- During **reset processing**:
    
    - Endur checks `index_historical_prices`:
        
        ini
        
        CopyEdit
        
        `reset_date = 2025-08-15 index = Platts GD`
        
    - Finds price = 3.50.
        
    - Applies this price in the deal’s Reset Tab for 2025-08-15.
        
    - Calculates payment = volume * 3.50.
        

---

## ✅ ✅ **Summary for your notes:**

|Aspect|Fixing|Reset|
|---|---|---|
|**What it is**|Price recording in the system|Application of the price to deals|
|**Stored in**|`index_historical_prices`|Deal’s Reset Tab|
|**Purpose**|Capture market prices|Calculate payments, MTM, settlement|
|**Relationship**|“Provides price for reset”|“Uses price from fixing”|

[[Resets and Fixings in Endur]]