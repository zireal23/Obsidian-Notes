## 🚩 1️⃣ Why they are **not just called "fix-float swaps"**

A **generic fixed-float swap** (like an interest rate swap) involves:

- One party paying **fixed**.
    
- The other party paying **floating** (e.g., LIBOR).
    
- Payments exchanged periodically.
    

In commodities, **fixed-floating swaps** can reference:

- A **monthly index price** (e.g., Platts Gas Daily for the month average).
    
- A **daily index price**.
    
- A **settlement index**.
    

**But they do not necessarily mimic futures contracts in structure or settlement timing.**

---

## 🚩 2️⃣ Why are these called **futures look-alike swaps?**

These swaps:  
✅ Are structured **to exactly replicate the financial exposure of a futures contract** for a delivery period.

✅ Instead of physically delivering gas:

- The **floating leg is settled at the same price used to settle futures**, typically:
    
    - **L3D** (average of the last 3 trading days settlement prices).
        
    - Or the **final futures settlement price**.
        

✅ The **fixed price is negotiated bilaterally**, but the **floating price references the futures settlement**.

---

## 🚩 3️⃣ What makes them "futures look-alike":

### ✅ **Same Pricing Reference:**

They use **futures settlement prices** (e.g., NYMEX L3D) for the floating leg.

### ✅ **Same Delivery Period:**

They match the **futures contract month** (e.g., April).

### ✅ **Similar PnL profile:**

- Buying a **futures look-alike swap** is **financially equivalent** to:
    
    - Buying a futures contract.
        
    - Rolling the futures position through expiry, cash-settling instead of taking delivery.
        

### ✅ **No physical delivery:**

Like financially settled futures, these swaps **settle financially, not physically**.

---

## 🚩 4️⃣ Why not call them simply "futures contracts"?

Because:  
✅ They are **bilateral OTC swaps** between two parties, not exchange-traded instruments.

✅ They **do not require margin posting** to the exchange or clearinghouse (unless cleared via a CCP).

✅ They are **flexible** in size and credit terms, unlike standardized futures.

✅ They **mimic the economics** of futures but **remain swaps in legal structure**.

---

## 🚩 5️⃣ Why does this distinction matter practically?

- For **accounting and reporting**, swaps and futures are different instruments.
    
- For **regulatory compliance**, swaps may be subject to different margining (e.g., uncleared margin rules).
    
- In **Endur**, these instruments will be modeled as swaps with references to futures settlement indices.
    

---

## ⚡ Summary

✅ These swaps are called **“futures look-alike swaps”** (or **“futures swaps”**) because:

- They **financially replicate futures contracts** using the **same pricing references and delivery periods**.
    
- They **remain bilateral OTC swaps**, not exchange-traded futures.
    
- They **settle financially using futures-based prices**.
    

✅ They are **not simply called "fix-float swaps"** because:

- A generic fix-float swap does not inherently tie to futures settlement mechanics.
    
- The “futures look-alike” term highlights the **explicit design to mimic futures contracts** for clients who want futures-like exposure without using futures directly.
[[Derivatives/Futures]]
