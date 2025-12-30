## 1. What a basis curve actually is (practitioner definition)

A **basis curve** is:

> A trader-constructed curve of **expected spreads** over a reference index (usually a futures-settled index), by location, product, or time bucket.

Formally:

`Physical Forward Price(t, T) = Index Forward Price(t, T) + Basis(t, T)`

Where:

- Index forward price → observable (exchange / swaps)
    
- **Basis(t, T)** → _not observable_, trader-estimated
    

➡️ **This curve does not come from the market.  
It comes from the trader’s brain.**

---

## 2. Why basis exists at all (economic reality)

Basis exists because **physical commodities are not fungible**.

Drivers:

- Location constraints (pipeline congestion, shipping)
    
- Quality differences
    
- Operational risk
    
- Storage & optionality
    
- Regulatory / contractual constraints
    
- Temporal mismatch (hourly vs monthly, daily vs ratable)
    

If basis didn’t exist:

> Everything would trade at the futures price  
> (which is obviously false in energy)

---

## 3. How traders actually construct a basis curve

This is where textbooks stop and **real trading starts**.

### Step 1: Anchor on the futures (or index) curve

- Futures curve = **market consensus**
    
- Highly liquid, transparent
    
- Trader _accepts_ this as given
    

This is **not where edge lives**.

---

### Step 2: Observe physical market signals

Sources:

- Bid-week prints
    
- Daily spot deals
    
- Broker color
    
- Flow data
    
- Pipeline nominations
    
- Storage levels
    
- Weather models
    
- Outages, maintenance
    
- Regulatory events
    

Most of this data is:

- Fragmented
    
- Delayed
    
- Noisy
    
- Non-public
    

---

### Step 3: Form a _view_ on dislocations

Trader asks:

- Is this hub going to tighten or loosen vs index?
    
- Will congestion clear or persist?
    
- Will volatility concentrate in certain days?
    
- Is the market mispricing optionality?
    

This becomes:

> “I think **Hub A – Index** will be +$0.18 in Jan, not +$0.05.”

That belief _is_ the basis curve point.

---

### Step 4: Shape the curve across time

Basis is **not flat**:

- Winter ≠ summer
    
- Shoulder months behave differently
    
- Event risk creates kinks
    

Traders shape:

- Monthly basis
    
- Seasonal basis
    
- Sometimes daily / hourly basis
    

This shaping is:

- Part data
    
- Part experience
    
- Part pattern recognition
    

---

## 4. Why basis curves are inherently subjective

There is **no single correct basis curve**.

Two senior traders:

- See the same futures curve
    
- See the same flows
    
- Build **different basis curves**
    

Why?

- Different mental models
    
- Different risk appetite
    
- Different physical access
    
- Different optionality embedded in their books
    

➡️ This is why:

> **Basis curves are proprietary intellectual capital**

---

## 5. Where profits actually come from 💰

A trader **rarely makes money by predicting futures direction**.

They make money by:

- Buying physical at _index + cheap basis_
    
- Selling at _index + rich basis_
    
- Capturing mispriced location or time spreads
    
- Monetizing optionality others ignore
    

In short:

`PnL ≈ (Realized Basis – Assumed Basis) × Volume`

If your basis view is better than the market:

- You win even if futures go sideways
    
- You may win even if futures go against you
    

---

## 6. Basis curves as the backbone of the book

Everything downstream depends on them:

- Physical deal valuation
    
- Swap pricing
    
- Optionality value
    
- Risk metrics (VaR, stress)
    
- Storage economics
    
- Transport economics
    

A **bad basis curve** means:

- Fake PnL
    
- False comfort
    
- Surprise losses
    

A **good basis curve** means:

- Stable returns
    
- Repeatable edge
    
- Institutional confidence
    

---

## 7. Why firms become dependent on individual traders ⚠️

Because:

- Basis curves live in people, not databases
    
- Illiquid markets lack verification
    
- Junior staff cannot easily challenge assumptions
    

This is why:

- Curve governance is hard
    
- Middle office tension exists
    
- Trader departures are traumatic
    

You already saw this hinted in the text — this is _exactly_ what they mean.

---

## 8. System & Endur implications (very important)

An ETRM must:

- Separate **market curves** (futures)
    
- From **trader curves** (basis)
    
- Track:
    
    - Who posted the curve
        
    - What assumptions were used
        
    - What changed and why
        

Best-practice systems:

- Lock curves after EOD
    
- Allow audit trails
    
- Flag large discretionary moves
    
- Allow scenario basis curves
    

This is not bureaucracy — it is **profit protection**.

---

## 9. Mental model to keep forever

Think like this:

`Futures curve = shared reality Basis curve   = trader belief PnL           = belief vs reality`

Or even more bluntly:

> **“Show me your basis curve, and I’ll tell you how you make money.”**