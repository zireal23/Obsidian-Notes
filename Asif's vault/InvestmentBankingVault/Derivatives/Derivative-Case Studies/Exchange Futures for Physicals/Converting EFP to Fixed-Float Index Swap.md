## ✅ Concept: Converting an EFP into a Fixed-Float Index Swap

An **Index Swap (Fixed-for-Floating)** is a financial instrument where you:

- **Pay a fixed price** (e.g., $1.75/MMBtu),
    
- **Receive a floating index price** (e.g., Permian Gas Daily Index).
    

It’s a **pure financial contract** — no physical gas is exchanged. The goal is to hedge or create synthetic exposure to the difference between **a fixed price and the local index**.

---

### 🧠 What’s Inside an EFP?

You buy a Permian EFP at:

- Posted Price = $2.00
    
- Differential = –$0.25
    
- Invoice = $1.75
    

Which gives you:

- ✅ Long physical gas at **Permian Index**
    
- ✅ Long basis swap (Index – $2.00 = –$0.25)
    
- ❌ Short futures at $2.00
    

---

## 🔧 Steps to Convert EFP → Index Swap

You’re trying to create a **Pay Fixed / Receive Index** financial swap. Here’s how you do it:

### Step 1: Convert EFP into a Basis Swap

- ✅ Sell the physical gas at **Index**
    
- ✅ Buy back the short futures  
    → You’re left with a long basis swap at –$0.25
    

### Step 2: Add a Futures Swap

- ✅ Pay fixed $2.00
    
- ✅ Receive L3D (or LTD) futures
    

### Resulting Position:

- ✅ Long Basis Swap: Index – L3D (at –$0.25)
    
- ✅ Long Futures Swap: L3D – $2.00  
    → Combine them:  
    **Index – $2.00 + $2.00 = Index**
    

You're now left with:

> ✅ Receive **Index**  
> ✅ Pay **$1.75**  
> ➡️ ✅ A synthetic **Fixed-Float Index Swap at $1.75**


![[Pasted image 20250611135127.png]]

---

## 🧮 Effective Price Logic

You paid $1.75 total (via EFP)  
You now receive **Index**  
So you're effectively in a swap that pays **$1.75 fixed** and receives **Index**

This lets you hedge a physical fixed-price gas sale or express a view on index strength.

---

## ✅ Summary

This process involves:

1. Converting EFP into a **Basis Swap**
    
2. Adding a **Futures Swap**  
    ➡️ Result: ✅ Synthetic **Index Swap** (Fixed-for-Floating)



![[Pasted image 20250611135037.png]]

[[Comparison between different instruments converted from an EFP]]
[[Exchange futures for physical- Key points]]
[[Exchange of futures for physical gas]]
[[How is a price differential(Basis) calculated.md]]