# 📘 Exchange of Futures for Physical (EFP) – Natural Gas Trading

## 🧠 What is an EFP?

An **EFP (Exchange of Futures for Physical)** is a negotiated transaction where:
🔹 One party transfers **futures contracts** to another,  
🔹 In exchange for **physical natural gas** delivered at a specified location (not Henry Hub).

It links the **futures market** (financial) with **physical gas delivery**, allowing market participants to:
- Convert financial hedges into physical delivery,
- Lock in basis and price components,
- Maintain flexibility on when to fix price.

---

## 🧩 Components of an EFP

🔹 **Posted Price**:  
Agreed price for the futures leg (typically matches exchange-traded futures at the time of trade to avoid margin issues).

🔹 **Differential**:  
Negotiated basis value between Henry Hub and the physical delivery point. Can be negative or positive depending on location.

🔹 **Invoice Price**:  
Amount the buyer pays for the gas.  
📌 Formula: `Invoice Price = Posted Price + Differential`

🔹 **Delivery Point**:  
Location where physical gas is delivered (e.g., Chicago, Permian).

🔹 **Size**:  
Volume of gas per day and corresponding number of futures contracts (e.g., 10,000 MMBtu/day = 1 NYMEX contract/day).

---

## 🔄 Transaction Flow – Buyer’s Side

✅ **Buyer of an EFP**:
- 🔸 Pays the **invoice price** for the gas (Posted + Differential),
- 🔸 Receives **physical gas** at the agreed delivery point,
- 🔸 **Transfers futures contracts** to the seller (effectively short futures at posted price).

✅ **Seller of an EFP**:
- 🔸 Receives invoice cash,
- 🔸 Delivers physical gas,
- 🔸 Receives futures contracts (effectively long futures at posted price).

---

## 🔧 Hedging Mechanics and Price Behavior

### 🎯 Effective Price Formula

After entering the EFP, the buyer's final **effective price** is:
Effective Price = Futures Buyback Price + EFP Differential

yaml
Copy
Edit

📌 **Invoice price cancels out** because the futures transfer is offset later by a buyback trade.

### 💡 Interpretation

- You’re **locking in the differential** (basis) at trade time.
- You have **full flexibility** to fix the outright price **later**, by buying back the short futures position at any time before expiry.

---

## 🔍 Example

- Posted Price: $2.00  
- Differential: –$0.30  
- Invoice: $1.70  
- Buyer transfers futures at $2.00 (short position)
- If buyer buys back futures at:
  - $2.45 → Effective Price = $2.45 + (–$0.30) = $2.15
  - $1.90 → Effective Price = $1.90 + (–$0.30) = $1.60

✅ Price flexibility comes from futures buyback, not invoice price.

---

## ⏳ When Does the EFP Settle?

🔹 **Futures Leg**:
- Settled immediately (same day as trade).
- Reported to the exchange as an **EFRP** (Exchange for Related Position).
- Futures are transferred from buyer to seller (or vice versa) on the day of the EFP.

🔹 **Physical Delivery Leg**:
- Occurs throughout the specified delivery month (e.g., May 1–31).
- Scheduled via NAESB standards.

🔹 **Gas Invoice**:
- Usually paid monthly by the 25th of the following month, unless daily settlement is agreed.

---

## 📉 What if Differential Moves After the EFP?

Once you enter the EFP:
✅ The **differential is fixed**, so you have **no further basis risk**.  
❌ You can't benefit from later improvements in the basis.  
But:
✅ You also won’t be hurt by adverse basis moves after the deal.

📌 Your effective price is now determined only by **when you buy back the futures**.

---

## ⚠️ Why Not Just Use a Fixed-Price Physical Forward?

If you sign a physical forward at a fixed price (e.g., $2.10 at Chicago):
- You’re **fully exposed to basis risk** if you try to hedge using Henry Hub futures.
- You don’t have flexibility — your price is locked.

✅ An EFP **locks the basis** (via the differential), and  
✅ Gives you **optional control over when to fix price** (via futures leg).  
✅ It bundles **futures + basis + physical gas** into one coherent trade.

---

## 🔁 Summary: Why Use an EFP?

| Feature                     | Physical Forward | Basis Swap Only | EFP                   |
|-----------------------------|------------------|------------------|------------------------|
| Physical delivery           | ✅ Yes            | ❌ No             | ✅ Yes                 |
| Basis exposure              | ✅ Yes            | ❌ Hedged         | ❌ Hedged via diff     |
| Price fix flexibility       | ❌ No             | ❌ No             | ✅ Yes (via futures)   |
| Futures exposure            | ❌ No             | ✅ Indirect       | ✅ Explicit            |
| Can hedge/index/swap later  | ❌ No             | ❌ No             | ✅ Yes (via conversion)|

---

## 🛠️ Use Cases

- ✅ Converting a **futures position** into a physical deal at a non-Henry Hub point.
- ✅ Locking **basis today** but fixing **price later**.
- ✅ Avoiding **delivery obligation** on exchange by moving to OTC.
- ✅ Gaining **pricing flexibility** with full operational delivery.
- ✅ Creating or converting **basis swaps, index gas, futures swaps**, etc.

---

## 🧰 Bonus: What EFPs Can Be Converted Into

An EFP can be **restructured into**:
- 🔸 Physical Index Gas (strip out basis + futures)
- 🔸 Fixed-Price Gas (strip out futures only)
- 🔸 Basis Swap (strip out index + futures)
- 🔸 Futures Swap (strip out index + basis)
- 🔸 Index Swap (via combination of steps above)

📌 This flexibility is what makes EFPs such a powerful tool in natural gas trading.

[[Exchange of futures for physical gas]]
[[Basis Swaps.md]]
[[Forward and Futures Contracts.md]]