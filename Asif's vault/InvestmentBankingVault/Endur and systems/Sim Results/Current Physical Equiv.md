### **Definition**

**Current Physical Equiv** represents the **currency equivalent value** of **physical flows** for the **current day** (i.e., flows whose payment date is today).  
It converts the _physical quantity_ into the _deal currency_ (USD, GBP, etc.), based on the valuation parameters used in the simulation.

---

### **How It’s Calculated**

It is derived from three other results:

- **Current Physical (Result 42):** the _physical quantity_ (e.g., barrels, MMBtu, tons) of today’s flow.
    
- **N.V. by Leg (Result 106):** the _notional value_ per leg, which helps translate the physical quantity into monetary terms.
    
- **Payment Date by Leg (Result 16):** ensures that only those flows with a payment date equal to the _current simulation date_ are considered.
    

So, in short:

> 🧾 **Current Physical Equiv = Current Physical × Price / FX rate (as relevant)**  
> and it’s expressed in the **deal currency**.

---

### **Scope**

- **Result ID:** 43
    
- **Result Enumeration:** `PHYSICAL_EQUIV_CURRENT_RESULT`
    
- **Result Class:** `Tran Result`
    
- **Applies to Toolsets:** Commodity, ComFut (v82R1+), EngyLTP, EngyTS, MetalSwap, Power, Swap.  
    (Some are retained only for backward compatibility.)
    

---

### **Interpretation in Simulation**

In simulation results (like EOD or ad hoc valuations):

- It shows **today’s physical delivery value** for the deal, in its **currency equivalent**.
    
- Useful for **daily P&L** tracking, especially for physical commodity deals where deliveries happen over multiple days.
    
- Combined with **Current Cash**, it gives a clear view of today’s realized activity — what was physically delivered and its monetary worth.
    

---

## 🗒️ **Obsidian Note**

**Title:** Endur Sim Result – Current Physical Equiv (Result ID 43)

**Definition:**  
Represents the currency equivalent (in deal currency) of physical flows for the current day.

**Dependencies:**

- Current Physical (#42)
    
- NV By Leg (#106)
    
- Payment Date By Leg (#16)
    

**Meaning:**  
The monetary value (in deal currency) of the physical quantity delivered today. It captures the value of today’s physical flow, not forecasted or historical flows.

**Result Class:** Tran Result  
**Result Enumeration:** PHYSICAL_EQUIV_CURRENT_RESULT  
**Toolsets:** Commodity, ComFut (v82R1+), EngyLTP, EngyTS, MetalSwap, Power, Swap  
**Purpose:** Used to calculate and monitor realized P&L from physical deliveries occurring on the current day.


## 🧩 The Situation

- You have a **physical deal** with a **June delivery profile** (say daily deliveries all through June).
    
- The **payment date** for that delivery month is **5th July**.
    
- By July 5th, all the physical deliveries are long done — nothing is physically flowing anymore.
    

Yet, when you run the simulation on **5th July**, you see a non-zero **Current Physical Equiv (Result 43)**.

---

## 🧠 Why That Happens

The key is to remember that:

> **Endur’s “Current” results are driven by the _payment date_, not necessarily the physical delivery date.**

Let’s look at what this specific result does:

|Component|What it Represents|What Current Physical Equiv Uses|
|---|---|---|
|**Current Physical (#42)**|The quantity of the flow whose **payment date = simulation date**.|✅ Used|
|**Payment Date By Leg (#16)**|The actual payment date of the flow.|✅ Used|
|**NV By Leg (#106)**|Converts the flow into a currency value.|✅ Used|

So, even if **physical delivery** occurred in June, Endur won’t mark its **“Current Physical Equiv”** until the **cash settlement date arrives (July 5th)** — because that’s when the **monetary realization** of the physical delivery actually happens in accounting/P&L terms.

---

## 💡 Conceptually

You can think of it like this:

|Date|Event|Endur’s Perspective|
|---|---|---|
|June (each day)|Physical deliveries happen|Reflected in **Projected Physical Equiv** results (future/forecasted values).|
|July 5|Payment occurs|The _value_ of those deliveries becomes **Current Physical Equiv** — i.e., today’s realized cash-equivalent of prior physical flows.|

So **Current Physical Equiv** tells you:

> “How much of my physical exposure has _settled today_ (in currency terms)?”

It’s _not_ about today’s delivery, but about **today’s settlement** of prior deliveries.

---

## 💰 Why It Matters

This distinction is crucial for:

- **Daily P&L** → because realized P&L recognizes the value on the payment date.
    
- **Cashflow tracking** → you can match physical equivalents with **Current Cash** to reconcile realized values vs. actual received cash.
    
- **Risk reporting** → this ensures today’s exposure reflects what’s been economically settled.
    

---


> 🔍 Although “Current Physical Equiv” represents the value of _today’s_ physical flow in currency terms, it is **driven by the payment date**, not the delivery date.  
> For example, if June deliveries have a payment date of 5th July, the entire June delivery value will appear as **Current Physical Equiv** on 5th July — reflecting the monetary realization of those deliveries rather than new physical activity.