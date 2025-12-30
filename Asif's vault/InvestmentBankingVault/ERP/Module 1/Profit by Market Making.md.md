## 1. What Kaminski means by “market making” (narrow definition)

He is **not** using the broad Wall Street definition.

Here, **market making =**

> being willing to quote **both a bid and an offer** to a customer and take **either side** of the trade.

### How money is made

- You buy at the bid
    
- You sell at the offer
    
- You capture the **bid–offer spread**
    

**Revenue drivers:**

1. **Transaction volume**
    
2. **Spread size**
    

👉 Wider spreads = less liquid markets & longer maturities  
👉 Higher volume = more liquid, shorter-dated markets

---

## 2. The hidden risk: warehousing risk

In illiquid or long-dated markets:

- You _can’t_ instantly offset the trade
    
- You must **warehouse risk** (hold it on your book)
    

That creates:

- **Price risk**
    
- **Liquidity risk**
    
- **Time risk**
    

Example:

- You quote a 5-year power hedge to a utility
    
- You can’t find an immediate offsetting buyer
    
- You sit with that exposure for months
    

So market making is **not free money** — especially outside liquid front months.

---

## 3. Stack-and-roll strategy (and why it’s dangerous)

### What is stack-and-roll?

Instead of hedging a long-dated exposure properly, you:

- Hedge the _entire long-term volume_ using **short-term instruments**
    
- As each contract nears expiry:
    
    - Close it
        
    - Roll into the next front-month contract
        

Example:

- 5-year gas exposure
    
- Hedge everything using the **front-month NYMEX gas future**
    
- Roll every month
    

### Why traders liked it

- Short-term instruments are liquid
    
- Tighter bid-offer spreads
    
- Easy execution
    

### Why it’s dangerous

1. **Roll risk**  
    Each roll costs money (spread + slippage)
    
2. **Market impact**  
    If the market discovers you _must_ roll:
    
    - Other traders **front-run** you
        
    - Prices move _against_ you
        
3. **Basis & curve risk**  
    Front-month ≠ long-dated exposure
    

This strategy **blew up MG Marketing & Refining**, becoming a textbook failure.

👉 **Key lesson:** Liquidity illusion is lethal.

---

## 4. Why pure bid–offer market making is low-margin

Kaminski uses **EnronOnline (EOL)** as a numerical example.

### Assumptions

- Spread: **$0.005 / MMBtu**
    
- Trades/day: **5,000**
    
- Contract size: **5,000 MMBtu**
    
- Trading days/year: **250**
    

### Result

➡ ~**$16 million per year**

That sounds big — but:

- Technology
    
- Infrastructure
    
- Risk
    
- Staff
    
- Compliance
    

👉 **Conclusion:**  
Pure electronic market making in liquid commodities is **low-margin and scale-dependent**.

This is _not_ where the really interesting money is.

---

## 5. The real money: “customer-oriented market making” (hedge intermediation)

This is the **most important part**.

### The setup

The intermediary (bank / trading firm) sits between:

- **Producer** (wants price certainty)
    
- **End user** (also wants price certainty)
    

Both hate risk — _for different reasons_.

---

### Producer behaviour

Producer expects future spot price:

E(ST)E(S_T)E(ST​)

But they’re willing to sell forward at a **discount** to eliminate risk:

E(ST)−fpE(S_T) - f_pE(ST​)−fp​

> fpf_pfp​ = _fear premium_ (Kaminski’s joke is intentional)

---

### End-user behaviour

End user expects the same spot price, but is willing to **pay extra** to remove uncertainty:

E(ST)+feE(S_T) + f_eE(ST​)+fe​

---

### Intermediary’s profit

The trading firm:

- Buys from producer at **lower price**
    
- Sells to end user at **higher price**
    

Profit captured:

fp+fef_p + f_efp​+fe​

This is called the **hedging spread**.

👉 This spread is:

- Much larger than bid–offer spreads
    
- More stable
    
- Scales with volume and tenor
    

This is **structural profit**, not trading genius.

---

## 6. Why opacity is essential to this business

If producers and end users **saw these spreads clearly**:

- They might trade directly
    
- Or new intermediaries would undercut margins
    

So hedge providers:

- Prefer **OTC markets**
    
- Prefer **customised contracts**
    
- Prefer **complex structures**
    

Why?

- Prices become **non-comparable**
    
- Margins are buried in:
    
    - embedded options
        
    - formulas
        
    - path-dependencies
        

👉 Transparency destroys rent extraction.

---

## 7. Why firms push long-term hedging

Long-dated hedges:

- Higher volumes
    
- Wider spreads
    
- Illiquid curves
    
- Less price transparency
    

So firms:

- Emphasise volatility
    
- Frame hedging as “responsible”
    
- Sometimes link hedging to financing relationships
    

Kaminski’s dark humour:

> “a terrified customer is a satisfied customer”

This is **emotional economics**, not just math.

---

## 8. Dodd–Frank resistance: the real reason

### Why banks opposed:

- Mandatory exchange trading
    
- Clearing
    
- Price reporting
    

Because it:

- Compresses spreads
    
- Removes opacity
    
- Turns bespoke hedges into commodities
    

### The surprise

Even **end users** opposed it.

Why?

- Bilateral hedges offer:
    
    - flexibility
        
    - credit arrangements
        
    - convenience
        
    - relationship benefits
        

They knowingly **pay more** in exchange for:

- simplicity
    
- certainty
    
- bundled services
    

This is _not_ ignorance — it’s a trade-off.

---

## 9. The deeper truth Kaminski hints at

Hedge providers **do provide real value**:

- Balance sheet
    
- Risk warehousing
    
- Structuring expertise
    
- Credit transformation
    

But…

> They would very much like to make _a little extra_ by keeping markets opaque.

That’s the honest equilibrium.

---
Some doubts:
1. Usually bid is lower and spread is higher, then isnt it a loss to capture the spread? 
2. 2.How does rolling a contract from near end to middle end future contract work and how does it cost money or slippage? 
3. How does other traders "front run"? 
4. 4.How is customer oriented market making any different? Is it because you always have a opposite position with another customer??? And if that is so why cant the trader and customer transact directly?

---

## 1. “Bid is lower and offer is higher — isn’t that a loss to capture the spread?”

This is a **very common mental trap**, so let’s slow down.

### What you’re implicitly imagining (wrong model)

You’re thinking:

> “I buy at the higher price and sell at the lower price.”

That _would_ be a loss — but that’s not what a market maker does.

---

### What actually happens

A market maker **quotes two prices simultaneously**:

- **Bid** = price at which _they will buy_
    
- **Offer (Ask)** = price at which _they will sell_
    

Example:

`Bid  = 100 Offer = 102`

Now two possible customer actions:

#### Case A: Customer sells to you

- You buy at **100**
    
- You now hold inventory
    

Later:

- Another customer buys from you at **102**
    

➡ **Profit = 2 (the spread)**

#### Case B: Reverse order

- Customer buys from you at **102**
    
- Later someone sells to you at **100**
    

➡ **Same profit**

---

### Why this is not risk-free

The risk is **inventory risk**, not pricing logic.

If:

- You buy at 100
    
- And the market moves to 95 before you can sell
    

Then:

- You lose **5**, which overwhelms the spread
    

👉 That’s why **liquidity + speed** matter.  
👉 In illiquid markets, spread ≠ guaranteed profit.

---

## 2. How rolling a contract works — and why it costs money

This is subtle but extremely important.

### Setup: long-dated exposure

Suppose you’ve sold a customer:

- 5 years of gas at fixed price
    
- Volume spread across 60 months
    

You are **short long-dated gas**.

---

### Proper hedge (ideal but illiquid)

- Hedge with 5-year swaps or forwards
    
- Problem: very illiquid, wide spreads
    

---

### Stack-and-roll hedge (what Kaminski describes)

Instead, you:

- Hedge **all 5 years’ volume** using **front-month futures**
    

Example:

- Total exposure = 1,000,000 MMBtu
    
- You hedge with **front-month NYMEX**
    

---

### What happens at expiry

1. Front-month contract approaches expiry
    
2. You must close it:
    
    - Sell if long
        
    - Buy if short
        
3. Then re-establish hedge in:
    
    - Next month contract
        

This is the **roll**.

---

### Where the cost comes from

#### (a) Bid–offer every time

Each roll:

- Pay spread on exit
    
- Pay spread on re-entry
    

Small per roll → huge over years.

---

#### (b) Term structure (contango / backwardation)

If market is in **contango**:

`Front month = 100 Next month  = 102`

Rolling long costs **+2 every month**.

That’s structural loss.

---

#### (c) Market impact

If the market knows:

- You _must_ roll
    
- And the size is large
    

Prices move **against you** while you execute.

---

## 3. What does “front-running” mean here?

This is **not illegal insider front-running**.  
This is **economic front-running**.

### Situation

Other traders realise:

- A large player _must_ roll a huge position
    
- And has no alternative
    

They act **before you**, not after.

---

### Example

You need to:

- Buy 10,000 contracts of next-month gas
    

Other traders:

1. Buy first
    
2. Push price up
    
3. Sell to you at a worse price
    

You pay:

- Higher execution price
    
- Larger slippage
    

They extract:

- Guaranteed profit
    

Kaminski’s phrase:

> “extract their pound of flesh”

This happens **purely because your position is predictable**.

---

## 4. How is customer-oriented market making different?

This is the _core conceptual leap_.

### Key difference

You are **not** making money from micro-spreads.

You are making money from **risk transformation**.

---

### Structure (simplified)

- Producer wants to **sell forward**
    
- End user wants to **buy forward**
    
- They don’t:
    
    - know each other
        
    - trust each other
        
    - want credit exposure
        
    - want legal complexity
        

You step in between.

---

### Do you always have opposite customers?

**Sometimes yes, often no, but eventually yes.**

- You might warehouse risk temporarily
    
- But over time, flows tend to balance
    

More importantly:

> You **don’t need perfect matching** to be profitable.

Your profit comes from:

(E(ST)−fp)↔(E(ST)+fe)(E(S_T) - f_p) \leftrightarrow (E(S_T) + f_e)(E(ST​)−fp​)↔(E(ST​)+fe​)

You capture:

fp+fef_p + f_efp​+fe​

This is **much larger and more stable** than a bid–offer spread.

---

### “Why can’t producer and customer trade directly?”

This is the most important question — and the answer is **not technical**, it’s **economic and institutional**.

#### 1. Credit risk

- Who posts collateral?
    
- What if one side defaults?
    
- Who manages margining?
    

Trading firm:

- Has balance sheet
    
- Manages credit professionally
    

---

#### 2. Mismatch of needs

- Volumes don’t line up
    
- Tenors don’t line up
    
- Optionality doesn’t line up
    

You absorb mismatches.

---

#### 3. Legal & operational complexity

- ISDA
    
- Credit support annexes
    
- Scheduling
    
- Settlement
    
- Regulatory reporting
    

Most producers/end users don’t want this burden.

---

#### 4. Price opacity is intentional

If:

- Prices were transparent
    
- Contracts were standardised
    

Margins would collapse.

Both intermediaries **and many customers** accept opacity in exchange for convenience and flexibility.

---

## The mental model you should lock in

### Exchange market making

- Thin margins
    
- High speed
    
- High volume
    
- High competition
    
- Low structural power
    

### Customer-oriented market making

- Wide spreads
    
- Long-dated
    
- Illiquid
    
- Relationship-driven
    
- Structurally defensible profits
    

This is why **origination desks are king**, and why **Endur exists at all**.