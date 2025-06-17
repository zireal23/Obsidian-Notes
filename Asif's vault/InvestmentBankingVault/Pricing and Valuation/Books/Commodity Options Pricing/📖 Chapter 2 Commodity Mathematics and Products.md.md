## What the Chapter is About:

- We begin with **one-factor models** (simple models where one thing — like the price of the commodity — drives everything).
    
- **First**, we revise basic Black-Scholes pricing for traded spot markets (what happens when you trade the asset directly).
    
- **Then**, we extend the discussion to **forwards** and **futures** markets — common in commodities.
    
- We discuss **peculiarities** of commodities (e.g., physical delivery delays, storage costs, etc.)
    
- **After that**, we move to options on commodities (the main topic of the book).
    
- **Finally**, the chapter touches on **advanced models**.
    

> **Goal:** Build from simple spot trading → forwards/futures → options → advanced topics.

---
# 2.1 Spot, Forwards, and Futures

### Key Concept:

- In commodities, **spot contracts** are **not always immediately settled** — they usually settle after a few days.
    
- In physical commodities (like oil, metals), **immediate delivery** is unrealistic because of logistics (shipping, storage, etc.).
    
- **Therefore**, most trading happens in **forwards** and **futures** — contracts that promise delivery at a future date.
    

---

### 👉 Important Points:

- **Spot Transaction**:
    
    - You agree today to buy/sell something.
        
    - But the actual exchange (settlement) happens a few business days later.
        
        - Example:
            
            - Buy on Monday (10 Sept 2012) → Settle on Wednesday (12 Sept 2012).
                
    - Metals: Settlement usually **T+2** (trade day + 2 business days).
        
    - Energy (like oil): Settlement usually **T+5**.
        
- **Problem for Commodities**:
    
    - You can't ship oil or copper in 2 days easily.
        
    - **Solution**: People trade **forwards** and **futures** instead of true spot.
        
- **Forward Contract**:
    
    - Agreement between two parties (over-the-counter).
        
    - Promise to buy/sell a quantity at a set price on a future date.
        
- **Futures Contract**:
    
    - Traded on an **exchange** (like NYMEX, ICE).
        
    - More standardized: Set quantities, set dates.
        
    - Exchange manages credit risk using **margins** (collateral).

---
# 📖 2.1.1 Spot (Detailed)

---

## ✨ What is a Spot Transaction?

At first glance, you might think a **spot transaction** means:

> "You pay today and get the goods today."

But in **real-world commodity markets**, that's **NOT** quite true.  
In commodities, **spot** usually means:

> "You agree today on the price, but you deliver and pay after a few days."

---

**Why the Delay?**

- Physical commodities (like oil, copper, wheat) **can't be moved instantly**.
    
- There's **logistics** involved:
    
    - Oil must be loaded onto tankers.
        
    - Copper needs to be weighed, packed, and shipped.
        
    - Wheat needs to be stored or transferred to silos.
        
- So it's **normal** that a "spot" deal actually **settles a few business days later**.
    

---

## 📅 Standard Settlement Times

Depending on the commodity, the "few days" can vary:

|Commodity Type|Typical Settlement|
|---|---|
|Precious and Base Metals (Gold, Silver, Copper)|T+2 (Trade Day + 2 Business Days)|
|Energy (Oil, Gas)|T+5 (Trade Day + 5 Business Days)|

**Example:**

- You buy gold on Monday, September 10, 2012.
    
- Settlement date = Wednesday, September 12, 2012 (2 business days later).
    

---

## 📚 Important Definitions

|Term|Meaning|
|---|---|
|Trade Date|The day you agree on the transaction.|
|Settlement Date|The day when money and commodity actually change hands.|

---

## ⚡ Real-World Example: Why Spot Isn't Immediate

Imagine you are a trader in **crude oil**.

- You want to buy 100,000 barrels of oil.
    
- You and the seller agree today on a price: $80/barrel.
    
- But it takes time to:
    
    - Find a tanker ship.
        
    - Inspect the oil.
        
    - Get customs and shipping paperwork ready.
        
- Therefore, you **settle** the deal a few days later (T+5 in oil markets).
    

If "spot" really meant "immediate", physical commodity trading would break down!

---

## 🔥 Special Case: Electricity

Electricity **cannot be stored** easily.

- When it's produced, it has to be consumed.
    
- **Spot** electricity trades are much closer to _instantaneous_ delivery.
    
- That's why electricity markets behave differently.
    

---

## 🤔 But Wait... What if There's No Spot Market?

For many commodities (especially soft commodities like cocoa, coffee),  
**no active spot market** exists at all!

Instead, traders use the **nearest expiring futures contract** as a **proxy** for the spot price.

This is called the **Prompt Future**.

---

## 🧠 Mathematical Notation

| Symbol                | Meaning                                     |
| --------------------- | ------------------------------------------- |
| $$ StS_tSt $$​        | Spot price at time ttt.                     |
| $T⃗(t)\vec{T}(t)T(t)$ | First futures expiry date _after_ time ttt. |

**Example of T⃗(t)\vec{T}(t)T(t):**

- Suppose today is January 15, 2025.
    
- Futures expire at the end of each month.
    
- Then the **prompt future** would expire on January 31, 2025.
    
- So: T⃗(t)=\vec{T}(t) =T(t)= January 31, 2025.
    

The arrow (→) over T reminds us:

- As time passes, the prompt future "moves forward" to the next expiry.