## ✅ What Does “Converting an EFP into Fixed-Price Physical Gas” Mean?

When you **buy an EFP**, you are receiving **physical gas at index** and inheriting a **short futures position**. You’ve also locked in a **differential** (basis) between your delivery point and Henry Hub.

To convert this EFP into **fixed-price gas**, the goal is to **remove the futures leg**, so you’re no longer floating with Henry Hub. Instead, you lock your final gas price today.

---

### 📘 Let's break it down:

Say you:

- Buy an EFP for **Permian** delivery.
    
- Posted price = $2.00 (L3D futures)
    
- Differential = –$0.25  
    → Invoice Price = $1.75
    

Your effective position from the EFP:

- **Long physical Permian index gas**
    
- **Long basis swap** at (Index – $2.00 = –$0.25)
    
- **Short futures** at $2.00
    

### 🔄 Now, to convert this into **fixed-price gas**, you do this:

- **Buy back the short futures position** at current market (say, also $2.00)
    
- This closes your futures exposure.
    

What’s left?

- Physical gas exposure remains.
    
- Your total outlay = **Futures price + EFP differential**  
    → $2.00 (futures buyback) + (–$0.25) = **$1.75**
    

So now, you are holding physical gas, and you’ve paid **$1.75 total**.  
✅ That’s **fixed-price physical gas**.

---

## 🧠 Intuition

You're removing the futures leg, and since the **EFP differential is fixed**, the moment you close the futures leg, your gas price is effectively **fixed at:**

> **Futures Buyback Price + Differential**

You’re still receiving the gas. But now the price is no longer floating with futures — you’ve locked it by covering the short.

---

## 🛠 Use Case

This is extremely useful when:

- You want **physical gas delivery**,
    
- But want to **fix your price** in advance or at a favorable moment.
    

This allows you to hedge physical delivery just like a fixed forward contract — but with more flexibility.

---

### 🧩 Breakdown – Example

- 🔹 EFP Purchase:
  - Posted Price (L3D Futures): $2.00  
  - EFP Differential: –$0.25  
  - Invoice Price Paid = $1.75

- 🔹 Components of EFP:
  - Long Permian index gas (physical)
  - Long Permian basis swap (–$0.25)
  - Short futures at $2.00

---

### 🛠 Conversion Step

1. ✅ **Buy back the short futures position** at $2.00
2. ❌ No need to touch basis or physical position

---

### 📌 Result

You're left with:
- Long physical Permian gas
- **Fixed purchase price = $2.00 (futures buyback) + (–$0.25) = $1.75**

✅ You now hold **fixed-price physical gas at $1.75**

---

### 🧠 Why This Works

The EFP inherently contains:
- A futures leg
- A basis swap
- A physical gas leg

By neutralizing just the futures leg:
- You lock in the net cost of gas at **Futures + Differential**
- This is functionally identical to having purchased **fixed-price gas** at that value

---

### 🔄 Summary Formula

| Component             | Value         |
|------------------------|---------------|
| Futures buyback        | $2.00         |
| EFP differential       | –$0.25        |
| ✅ Fixed gas price     | $1.75         |[]
[[Exchange of futures for physical gas]]
[[Exchange futures for physical- Key points]]
[[Commodity Futures.md]]