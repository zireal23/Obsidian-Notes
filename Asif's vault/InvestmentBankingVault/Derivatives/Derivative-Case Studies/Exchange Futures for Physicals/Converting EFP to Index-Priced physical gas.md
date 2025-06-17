## 🔍 Understanding the Implicit Basis Swap in an EFP

### ❓ My Doubt:
> In an EFP, I’m essentially:
> - Selling a futures contract,
> - Paying **index – differential** for the gas,
> - Receiving physical gas.
> 
> So where exactly does the **basis swap** come into play?

---

### ✅ Concept: Basis Swap in EFPs Is **Implicit**, Not Traded Separately

Although you don't explicitly enter into a basis swap when doing an EFP, the structure of the EFP **mathematically includes a basis swap** between the local index price and Henry Hub futures.

---

### 🧩 Breakdown of a Long EFP Position

When you **buy an EFP**, you're doing the following:
- 🔹 **Paying** the invoice price = Posted Futures Price + Differential (e.g., $2.00 – $0.25 = $1.75)
- 🔹 **Receiving** physical gas at the **local index price**
- 🔹 **Transferring futures contracts** at the posted price (you become **short futures**)

This setup **replicates** the following 3 legs:
1. ✅ **Buy Index Gas** → You're taking physical delivery at index.
2. ✅ **Sell Futures @ P** → You’re short futures via the transfer.
3. ✅ **Pay P + Differential** → Matches your cash outflow.

---

### 🧠 How This Implies a Basis Swap

Let’s break it down algebraically:

You're:
- Long Index Gas
- Short Futures at `P`
- Net payment = `P + Differential`

So your total exposure = Index – Futures = Differential  
Which is exactly what a **basis swap** pays or costs.

📌 Therefore, **the EFP differential is functionally equivalent to the basis swap differential.**

---

### 📊 Visual Summary

| EFP Component             | Matches This Instrument      |
|---------------------------|------------------------------|
| Physical Gas at Index     | Index leg of physical trade  |
| Futures Transfer (short)  | Henry Hub leg of hedge       |
| Differential              | Basis Swap (Index – Futures) |

---

### 🔄 Why This Matters

Because the EFP includes a basis swap implicitly:
- You can **"strip it out"** by entering an **opposite basis swap trade**.
- You can compare the **EFP differential to the current basis market** to detect **arbitrage** (e.g., EFP diff = –$0.25, but market basis swap is –$0.20 → you’re getting a better deal in EFP).
- You understand that EFP = Futures + Basis + Physical Gas.

---

### 🎯 Recap

> Even though I never explicitly trade a basis swap in an EFP, I’m effectively long (or short) basis **because the combination of index gas + futures always implies a basis swap**.

✅ Yes — your understanding is correct:
- You **sell a future** (via transfer),
- You **pay index – differential** for physical gas,
- You **receive the gas**,
- → And the **differential = basis** that you implicitly locked in.

![[Pasted image 20250611131958.png]]

![[Pasted image 20250611132030.png]]

![[Pasted image 20250611132059.png]]

[[Exchange futures for physical- Key points]]
[[Basis Swaps.md]]
[[Commodity Futures.md]]