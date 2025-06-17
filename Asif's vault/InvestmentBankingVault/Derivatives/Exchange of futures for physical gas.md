### Exchange of Futures for Physical (EFP) – Natural Gas Trading

**Definition:**  
An EFP is a negotiated transaction in which one party transfers futures contracts to another in exchange for physical natural gas. It allows market participants to tie futures positions to physical delivery at non-standard delivery points (i.e., locations other than Henry Hub).

---

### Core Components of an EFP

1. **Posted Price:**  
    The price at which the futures contracts are transferred between accounts. This is a mutually agreed number, often close to the prevailing market futures price to minimize margin impacts.
    
2. **Differential (EFP Differential):**  
    The negotiated difference between the posted price and the invoice price of the physical gas. It reflects the basis between the futures market and the physical market location.
    
3. **Delivery Point:**  
    The location at which the physical gas is delivered. Unlike futures, which settle at Henry Hub, EFPs allow delivery at alternate points (e.g., Chicago, Permian, Transco).
    
4. **Size:**  
    Volume of gas per day (e.g., 10,000 MMBtu/day) and the equivalent number of futures contracts.
    
5. **Invoice Price:**  
    The actual price paid for the physical gas by the buyer. It is calculated as:  
    `Invoice Price = Posted Price + EFP Differential`
    
6. **Gas Quality:**  
    Must meet the standard of the futures contract specifications.
    

---

### Mechanics of an EFP

**Buyer Actions:**

- Pays the invoice price (posted price + differential).
    
- Receives physical gas at the agreed delivery point.
    
- Transfers futures contracts (valued at posted price) to the seller.
    

**Seller Actions:**

- Receives the invoice price.
    
- Delivers physical gas.
    
- Receives futures contracts from the buyer’s futures account.
    

---

### Algebraic Representation of EFP

An EFP can be broken into three components:

- A **basis swap**
    
- A **physical index gas transaction**
    
- A **futures position**
    

This leads to the following breakdown:

- **Long EFP =** long basis swap + long index gas – short futures
    
- **Short EFP =** short basis swap + short index gas + long futures
    

Thus:

- Buying an EFP is equivalent to buying gas at index, buying the basis, and selling futures.
    
- Selling an EFP is equivalent to selling gas at index, selling the basis, and buying futures.
    

---

### Effective Price Calculation

For the **buyer**, the effective purchase price depends on the price at which they later buy futures to cover the short position.

Example:

- Posted Price = $2.00
    
- Differential = –$0.30
    
- Invoice Price = $1.70
    
- If buyer covers futures at $2.45:
    
    - Effective Price = $2.00 – $2.45 – $1.70 = –$2.15 → drop negative sign → $2.15
        
- If buyer covers futures at $1.90:
    
    - Effective Price = $2.00 – $1.90 – $1.70 = –$1.60 → drop negative sign → $1.60
        

For the **seller**, the effective sale price depends on the price at which they sell the futures received.

Example:

- Invoice Price = $1.70
    
- Receives futures at $2.00
    
- If seller sells futures at $2.45:
    
    - Effective Sale Price = $1.70 – $2.00 + $2.45 = $2.15
        
- If seller sells futures at $1.90:
    
    - Effective Sale Price = $1.70 – $2.00 + $1.90 = $1.60
        

Key Insight: The invoice price doesn’t affect the effective price. Only the futures cover/sale price and the differential do.

---

### Strategic Use of EFPs

1. **Lock in Fixed Prices:**  
    Buyers and sellers can independently fix effective prices depending on futures market conditions.
    
2. **Hedge Physical Delivery Needs:**  
    EFPs allow entities holding futures positions to convert them into physical gas at non-Henry Hub points.
    
3. **Basis Arbitrage:**  
    Traders can profit from differences between EFP differentials and basis swap differentials.
    
4. **Liquidity Tool:**  
    EFPs often constitute ~90% of the volume taken to delivery at Henry Hub or alternate points.
    
5. **Margin Management:**  
    To avoid high margin requirements, posted prices are often aligned with current market futures prices or set closer to expiration.
    

---

### Converting EFPs into Other Instruments

1. **To Physical Index Gas:**
    
    - Sell basis swap and cover futures.
        
    - Results in a net physical index gas position.
        
2. **To Fixed-Price Gas:**
    
    - Only cover futures (don't unwind basis).
        
    - Results in physical gas at a fixed effective price.
        
3. **To Basis Swap:**
    
    - Sell physical gas at index and cover futures.
        
    - Results in a basis swap position.
        
4. **To Futures Swap:**
    
    - Strip out both physical gas and basis.
        
    - Leaves a swap between fixed price and L3D futures.
        
5. **To Fixed-Float Index Swap:**
    
    - Convert to basis swap and add futures swap.
        
    - Results in an index swap (e.g., pay fixed, receive index).
        

---

### Basis Risk in EFPs

Basis risk arises when the change in EFP differential does not track the futures price movement. For example:

- Day 1: Futures = $2.00, EFP diff = –$0.25 → Implied fixed price = $1.75
    
- Day 2: Futures = $2.15, EFP diff = –$0.20 → Implied fixed price = $1.95
    

Even if futures moved up $0.15, fixed price rose by $0.20 due to basis shift.

---

### Timing Considerations

The order of operations is flexible:

- You can initiate futures first, then do EFP.
    
- Or do the EFP first and cover futures later.
    

Timing affects the effective pricing. Traders often optimize when to execute futures leg to get the best net outcome.

---

### Summary

EFPs are versatile instruments used by natural gas traders to:

- Convert futures into physical delivery at custom locations.
    
- Lock in effective fixed prices.
    
- Hedge index or basis exposure.
    
- Create or unwind more complex positions (like swaps).
    
- Optimize execution based on futures market behavior.
    

Their flexibility, hedging utility, and conversion ability make EFPs a key building block in natural gas trading.