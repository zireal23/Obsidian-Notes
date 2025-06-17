
---
## 🧮 How Price Differential (Basis) is Calculated in Commodity Forwards

In natural gas and other physical commodity trades, the **price differential** (also called **basis**) reflects the cost difference between the **index hub price** (like NYMEX Henry Hub) and the **actual delivery location**.

---

### 📌 What is a Basis?

A **basis** is the adjustment added to (or subtracted from) an index price to reflect:

- **Transportation cost**
- **Local supply/demand imbalance**
- **Storage availability**
- **Market liquidity or congestion**
- **Weather-driven spikes**

---

### 🔢 Basis Pricing Formula

Final Price = Index Price + Basis Differential
- If the delivery point is *more expensive* than the hub → **positive basis**
- If the delivery point is *cheaper* than the hub → **negative basis**

---

### 🔄 Example Calculation

Let’s say:

- **Index Hub**: NYMEX Henry Hub
- **Delivery Location**: Transco Zone 6 NY
- **Index Price** (on July 10): `$2.75/MMBtu`
- **Agreed Basis**: `+$0.85/MMBtu`

Then:
Effective Trade Price = 2.75 + 0.85 = $3.60/MMBtu


---

### 💡 How is the Basis Agreed?

- Negotiated between **marketer and customer**
- Reflects **market fundamentals** and **pipeline tariffs**
- Traders often refer to **historical spreads** and **basis curve forwards**

---

### 📊 In Endur

In **Endur**, the basis can be:

- A **static dollar value** (e.g., `+0.85`)
- A **basis curve** (dynamic, varies by day/month)
- Entered in the **Pricing Tab** during deal capture
- Applied to each day during pricing and valuation

---

### 🧠 Tip from Traders

> "The basis tells you what the local market is doing. You can be long Henry Hub but short Chicago just by changing basis."

---



