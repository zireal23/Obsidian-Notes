## ✅ Concept: Converting an EFP into a Futures Swap

### 🎯 What is a Futures Swap?

A **futures swap** is a financial contract where you exchange:

- A **fixed price** (e.g., $2.00),
    
- For the **settlement value of futures** (e.g., L3D or LTD — Last Trading Day futures).
    

It’s a pure **financial instrument**, with **no physical gas** and **no basis exposure**. You're simply betting on where futures settle.

---

## 🧩 What’s Inside an EFP?

Let’s say you bought a Permian EFP:

- **Posted Price (P)** = $2.00
    
- **EFP Differential (D)** = –$0.25
    
- **Invoice Paid = $1.75**
    

From the EFP, you’re exposed to:

1. ✅ Physical gas at Permian Index
    
2. ✅ Basis swap at (Index – $2.00 = –$0.25)
    
3. ❌ Short Futures at $2.00
    

---

## 🔁 To convert this EFP into a **Futures Swap**, you must strip out:

1. ❌ **Physical gas**: Sell it at Index
    
2. ❌ **Basis swap**: Sell a basis swap at –$0.25
    
3. ✅ Leave the short futures position in place
    

You now hold:

- A short futures position at $2.00
    
- You've removed both the index and basis exposure
    

To complete the transformation into a **futures swap**, you would:

- Agree to **pay $2.00 fixed**
    
- Receive **LTD futures settlement value**
    

---

## 🧠 Net Result

- You’re now holding a **financial short futures swap**
    
- Valued as: **Fixed $2.00 vs. floating futures (LTD or L3D)**
    

You're essentially speculating that futures will **settle lower than $2.00**, or hedging exposure to a futures decline.

---

## 📌 Summary of Steps

- Step 1: Pay EFP invoice → $1.75
    
- Step 2: Sell physical gas → receive Index
    
- Step 3: Sell basis swap at –$0.25 → receive Index – $2.00
    
- Step 4: Buy back futures at $2.00 → net out futures exposure
    

After all cash flows cancel:

- You're left with a swap: **Pay fixed $2.00, receive floating futures settlement**

![[Pasted image 20250611134816.png]]

![[Pasted image 20250611134850.png]]
[[Comparison between different instruments converted from an EFP]]
[[Futures Price vs Spot Price.md]]
[[Exchange futures for physical- Key points]]
[[Exchange of futures for physical gas]]