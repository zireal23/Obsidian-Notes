## What “bid week” really is

**Bid week** is a _market convention_, not a law.

- Typically occurs **near the end of the month**
    
- Market participants trade **physical next-month volumes**
    
- Deals are reported to **price reporting agencies (PRAs)** like Platts, Argus, ICE
    
- The PRA calculates a **monthly index price** (often volume-weighted average)
    

This index then becomes the **settlement reference** for:

- Physical supply contracts
    
- Basis deals
    
- Swaps and some futures convergence logic
    

---

## When index prices _are_ determined in bid week ✅

This is common when:

- The commodity is **pipeline / logistics constrained**
    
- Delivery is **ratable over the month**
    
- Physical trading concentrates in a narrow window
    

### Examples

- **US Natural Gas (Henry Hub)**
    
    - Monthly physical index = largely bid-week trades
        
    - Published on **1st business day of delivery month**
        
- **Many North American gas hubs**
    
- **Some refined product markets**
    

In these cases:

> The “index price” ≈ _bid-week forward price for that physical month_

But even here, the index is **not a pure forward** — it is an **observed physical average**.

---

## When index prices are _not_ strictly bid-week based ❌

### 1. Daily index–based markets

Some markets use:

- **Daily spot indices**
    
- Monthly price = **average of daily prices**
    

Examples:

- Power markets (many regions)
    
- Some gas markets outside North America
    

Here:

> The monthly index is an **ex-post average**, not a bid-week construct

---

### 2. Thin or relationship-driven markets

- Few reported trades
    
- Heavy use of:
    
    - Bilateral relationships
        
    - Formula pricing
        
    - Broker indications
        

In such cases:

- PRAs may:
    
    - Use **assessment methodologies**
        
    - Combine bids, offers, trades, judgment
        

➡️ The “index” may be **partly model-based**

---

### 3. Markets where futures dominate price formation

Sometimes:

- Physical trades **reference futures prices**
    
- Example:
    
    - Physical price = Futures settlement ± basis
        

In these cases:

> Bid week is influenced by futures, not the other way around

This creates the **feedback loop** the book alludes to.

---

## Key conceptual distinction (very important)

An **index price is not defined by _when_ trades happen**, but by:

- **What transactions are eligible**
    
- **How they are weighted**
    
- **Who reports them**
    
- **What methodology the PRA applies**
    

Bid week is just:

> A _liquidity concentration mechanism_

---

## Why this matters in practice (Endur / ETRM lens)

You must **never assume**:

- “Index price = bid-week forward price”
    

Instead, systems must know:

- Which PRA?
    
- Which methodology?
    
- Which delivery point?
    
- Which averaging rule?
    
- Publication timing?
    

This affects:

- Cashflow timing
    
- P&L recognition
    
- Risk
    
- Futures convergence assumptions
    
- Back-office settlements
    

---

## Mental model to keep

Think in layers:

`Physical trades (bid week, daily, bilateral)         ↓ Price Reporting Agency methodology         ↓ Index price (monthly / daily)         ↓ Swaps, basis deals, futures convergence`

---

## Bottom line

- ❌ Index prices are **not always determined in bid week**
    
- ✅ Bid week is **common**, especially in US gas
    
- ⚠️ Index prices are **methodology-driven**, not time-window-driven
    
- 💡 Futures, forwards, and physicals co-determine each other