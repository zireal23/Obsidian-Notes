## 1. Core Idea of Storage Theory

- **Storage theory**, also called **convenience yield theory**, focuses on **inventories and storage** in commodity markets.
    
- It explains how **spot prices today** and **forward prices in the future** are linked through **interest rates, storage costs, and arbitrage**.
    
- Intuition: owning the physical commodity has **value beyond just the price**, because it allows you to **deliver when needed**, hedge shortages, or exploit market opportunities.
    

---

## 2. The Forward Price Formula

The forward price f(t,T)f(t,T)f(t,T) is given by:

f(t,T)=S(t)⋅(1+r+s)T−tf(t,T) = S(t) \cdot (1 + r + s)^{T-t}f(t,T)=S(t)⋅(1+r+s)T−t

Where:

- S(t)S(t)S(t) = spot price at time ttt
    
- rrr = annualized interest rate (cost of financing commodity purchase)
    
- sss = annualized storage cost per unit
    
- T−tT-tT−t = time to forward contract maturity (in years)
    

**Intuition:**

- The forward price is the **spot price adjusted for the cost of carrying** the commodity to the future date.
    
- If storage costs or financing costs are high, the forward price rises relative to spot.
    

---

## 3. Arbitrage Logic

Storage theory is based on **replication/arbitrage**:

### Upper Bound

- If forward price fff is **too high** relative to spot + storage + interest:
    

f>S⋅(1+r+s)T−tf > S \cdot (1 + r + s)^{T-t}f>S⋅(1+r+s)T−t

- Arbitrage:
    
    1. Borrow money at rate rrr
        
    2. Buy the commodity at spot price SSS
        
    3. Store it (pay cost sss)
        
    4. Sell a forward contract at fff
        
- At maturity, deliver the commodity into the forward contract → **lock in risk-free profit**
    

---

### Lower Bound

- If forward price fff is **too low** relative to spot + costs:
    

f<S⋅(1+r+s)T−tf < S \cdot (1 + r + s)^{T-t}f<S⋅(1+r+s)T−t

- Arbitrage:
    
    1. Sell commodity in the spot market today
        
    2. Invest proceeds at interest rate rrr
        
    3. Rent storage if needed
        
    4. Take a long forward position (agree to buy commodity back at fff)
        
- At maturity, receive the commodity via forward contract → **lock in profit**
    

**Conclusion:**

- In a **competitive market**, these arbitrage trades force:
    

f(t,T)≈S(t)⋅(1+r+s)T−tf(t,T) \approx S(t) \cdot (1 + r + s)^{T-t}f(t,T)≈S(t)⋅(1+r+s)T−t

> This is why **forward prices track spot prices plus carrying costs**.

---

## 4. Spot-Forward Convergence

- As time to delivery decreases (T−t→0)(T-t \to 0)(T−t→0):
    

f(t,T)→S(t)f(t,T) \to S(t)f(t,T)→S(t)

- Intuition: when the contract is about to expire, the forward price **must equal the spot price**, because physical delivery occurs immediately.
    

---

## 5. Market Frictions and Imperfections

- In practice, **exact equality rarely holds**, because of:
    
    - Bid-offer spreads
        
    - Transaction costs
        
    - Unequal access to storage and infrastructure
        
    - Restrictions on short selling
        
- These frictions mean forward prices **generally follow the formula** but may **deviate temporarily**.
    

---

## 6. Summary of Storage Theory Insights

1. Forward price = Spot + Financing + Storage (cost-of-carry)
    
2. Inventories are critical: higher inventories can reduce convenience yield → lower forward relative to spot
    
3. Arbitrage enforces **upper and lower bounds** on forward price
    
4. Spot and forward **converge as maturity approaches**
    
5. Market frictions cause **small deviations**, but overall tendency holds
    

---

✅ **Intuition:**

- **Holding physical commodities has value** → it gives you the ability to deliver, hedge, or exploit price differences
    
- Forward prices are **anchored to spot prices + carrying costs**
    
- The **storage cost** and **interest rate** are the main drivers of the forward curve, while **inventory scarcity** (convenience yield) can push forwards below the “pure cost-of-carry” level