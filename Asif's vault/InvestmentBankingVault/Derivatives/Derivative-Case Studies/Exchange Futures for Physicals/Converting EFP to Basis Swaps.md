## 🔁 Converting an EFP into a Basis Swap

### 📘 Concept

To convert a long EFP into a **basis swap**, you need to:
- ❌ Remove the physical gas exposure (sell gas at index),
- ❌ Close the futures leg (buy back the short futures),
- ✅ Keep the embedded differential between index and futures (i.e., basis).

---

### 🧩 Example – Step-by-Step

Assume:
- 📌 Posted Price (Futures) = $2.00 (L3D)
- 📌 EFP Differential = –$0.25
- 📌 Invoice Price Paid = $1.75

Your EFP position includes:
- ✅ Long Permian index gas
- ✅ Long basis swap at (Index – $2.00 = –$0.25)
- ❌ Short futures at $2.00

---

### 🔧 Conversion Steps

1. ✅ **Sell physical gas** at Permian index → removes index leg
2. ✅ **Buy back futures** at $2.00 → closes short leg

---

### 📌 Result

You're left with:
- ✅ A **long basis swap at –$0.25** (i.e., Index – $2.00)

This position will now profit or lose based on changes in the **basis** (difference between Permian index and Henry Hub futures).

---

### 🧠 Summary of Components

| EFP Component         | Converted Into |
|------------------------|----------------|
| Physical index gas     | ❌ Sold         |
| Short futures          | ❌ Closed       |
| EFP differential       | ✅ Basis swap   |

✅ Final Result = Long Permian Basis Swap @ –$0.25

---

### 🔄 Use Cases

- Express views on **basis movement** without holding physical gas
- Hedge basis exposure for indexed contracts
- Strip out physical volume while keeping price spread
## 🎯 Objective:

Convert a **long EFP** into a **basis swap** by:

- Selling the **physical gas** at index,
    
- Buying back the **short futures**.
    

What you're left with: **Net cash flow that behaves like a basis swap.**

---

## 🧾 Example Setup

You **buy a Permian EFP**:

- 📌 **Posted Price (P)** = $2.00 (L3D)
    
- 📌 **EFP Differential** = –$0.25
    
- 📌 **Invoice Price Paid** = $2.00 – $0.25 = **$1.75**
    
- You **transfer futures contracts** at $2.00 (i.e., you're now short at $2.00)
    
- You receive **physical gas at Permian Index**
    

---

## 🔧 Now: Convert to Basis Swap

You perform:

1. **Sell physical gas** at Index → receive cash = **Index**
    
2. **Buy back futures** at L3D = $2.00 → pay **$2.00**
    

---

## 💰 Full Cash Flow Breakdown

|Transaction|Direction|Amount|
|---|---|---|
|Pay invoice for EFP|Outflow|– $1.75|
|Transfer futures (short at $2.00)|None yet|(Position only)|
|Sell physical gas at Permian Index|Inflow|+ Index|
|Buy back futures at $2.00|Outflow|– $2.00|

---

## 🧮 Net Cash Flow

pgsql

CopyEdit

`= (– $1.75) + Index – $2.00 = Index – $3.75`

But remember: the **short futures were transferred at $2.00**, so to properly isolate the basis swap effect, break it down further:

---

## 📊 Rearranged View (Isolating Each Leg)

|Step|Value|
|---|---|
|**Step 1**: EFP Invoice Paid|– (Posted + Differential) = – $1.75|
|**Step 2**: Transfer futures @ $2.00|Implicit short|
|**Step 3**: Sell gas at Index|+ Index|
|**Step 4**: Buy back futures @ $2.00|– $2.00|

---

## 🔁 Combine and Simplify

Let's express the **total gain/loss** as:

pgsql

CopyEdit

`Total = Index – $2.00 – (Invoice Paid – $2.00)        = Index – $2.00 – (P + D – P)        = Index – $2.00 – D`

So:

pgsql

CopyEdit

`Net Cash Flow = Index – Futures Price – Differential               = (Index – Futures Price) – Differential`

But in our example:

- Index – Futures = basis
    
- EFP Differential = locked basis
    

So net cash = **Difference between basis and differential**

---

### ✅ Final Result:

- If **basis = differential**, your cash flow = **$0** → you’re left with **pure basis exposure**.
    
- If **basis ≠ differential**, your cash flow = difference → your basis swap is now **profitable or loss-making** depending on the mismatch.
    

---

## 🧠 Interpretation

You’ve stripped out index and futures legs, and all your cash flow now **moves with the basis** (i.e., Index – Futures).

That’s exactly what a **basis swap** does:

- If **basis widens** (more negative), your long basis swap **loses**.
    
- If **basis tightens** (less negative or goes positive), your long basis swap **gains**.


## 💡 EFP Invoice Adjustment – Why We Subtract the Futures Price

### ❓ Question
> Why do we subtract the **posted futures price** from the **invoice paid** when calculating cash flows during EFP conversion (e.g., when converting to a basis swap)?

---

### ✅ Short Answer
The **invoice price already includes the value of the futures** that you transferred as part of the EFP.  
But when you're calculating cash flows, you also **explicitly account for the futures buyback**.  
So to avoid **double-counting the futures leg**, you subtract the posted futures price once from the invoice.

---

### 🧩 Example Setup

- **Posted Price (P)** = $2.00  
- **EFP Differential (D)** = –$0.25  
- **Invoice Paid** = `P + D = $2.00 – $0.25 = $1.75`  
- You **transferred futures at $2.00** (short position)  
- You **buy back futures** at $2.00  
- You **sell gas** at Index

---

### 🧮 Net Cash Flow Formula (EFP → Basis Swap)
Net Cash Flow = Index – $2.00 – (Invoice Paid – $2.00)
This adjusts for:

- ✅ The gas sale (Index)
    
- ✅ The futures buyback (– $2.00)
    
- ✅ The embedded futures transfer already in the invoice (– ($1.75 – $2.00))

Net = Index – Futures – Differential
     = Basis – Differential
 ### 🧠 Intuition Behind Subtracting $2.00 from Invoice

- The **EFP invoice ($1.75)** is a bundle:
    
    - Payment for physical gas at index
        
    - Payment for the embedded **short futures position**
        
- When we **buy back futures separately**, we’re fully accounting for the futures leg
    
- But we haven't explicitly shown the **transfer** of short futures in the cash flows
    
- Subtracting `$2.00` from the invoice ensures we isolate the **basis differential**
    

---

### 📊 Tabular Flow Summary

| Action                              | Value                       |
| ----------------------------------- | --------------------------- |
| Invoice Paid                        | – $1.75                     |
| Futures Buyback                     | – $2.00                     |
| Gas Sale at Index                   | + Index                     |
| Invoice Adjustment (remove futures) | + ($2.00 – $1.75) = + $0.25 |

### 🎯 Final Takeaway

The `$2.00` subtracted from the invoice isn't a real cash flow — it's an **adjustment to remove the futures value** already baked into the invoice.

This ensures the cash flow analysis focuses only on the **basis leg**, once you've removed the physical and futures exposure.

📌 **This logic underpins why the EFP is equivalent to a bundle of:**

- 🔹 Index Gas
    
- 🔹 Futures
    
- 🔹 Basis Swap (Differential)

### 🔁 Reference Formula Recap
`Net Cash Flow = Index – Futures – Differential               = Basis – Differential`

Use this when:

- ✅ Converting EFP to basis swap
    
- ✅ Analyzing basis arbitrage
    
- ✅ Verifying differential PnL against current market basis

[[Exchange futures for physical- Key points]]
[[Exchange of futures for physical gas]]
[[Basis Swaps.md]]
[[Commodity Futures.md]]