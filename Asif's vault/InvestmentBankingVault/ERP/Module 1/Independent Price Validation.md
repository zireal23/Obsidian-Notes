## 1. The core principle of curve governance

> **The person who makes money from a curve cannot be the final authority on that curve.**

Everything else flows from this.

Curve governance exists to:

- Prevent **intentional manipulation**
    
- Catch **unintentional bias**
    
- Ensure **PnL is real, not model-generated**
    
- Protect the firm from **key-person risk**
    

---

## 2. Who owns what (clear separation of duties)

### Front Office (Traders)

- Propose and post:
    
    - Basis curves
        
    - Illiquid forward points
        
    - Shaped curves (seasonal / locational)
        
- Provide:
    
    - Market colour
        
    - Rationale for changes
        
- **Do NOT have final approval**
    

---

### Market Risk / Middle Office (Curve Governance Owner) ✅

This is the **independent control function**.

Typical titles:

- Market Risk
    
- Valuation Control
    
- Product Control
    
- IPV team (Independent Price Verification)
    

They:

- Validate curves **independently of PnL incentives**
    
- Own the **official valuation curves**
    
- Control curve sign-off
    
- Escalate disputes
    

This team **reports outside the trading line**.

---

### Back Office / Finance

- Uses **approved curves only**
    
- Books PnL, settlements, financial statements
    
- Zero discretion on prices
    

---

## 3. What Independent Price Verification (IPV) actually does

IPV is not theoretical — it is **daily operational work**.

### Sources used by IPV

- Exchange settlements (CME, ICE)
    
- Broker quotes (multiple brokers)
    
- PRAs (Platts, Argus)
    
- Consultant curves
    
- Historical prints
    
- Internal deal data (with caution)
    

They explicitly:

- **Do not trust trader curves by default**
    

---

## 4. How curve validation works in practice (daily cycle)

### Step 1: Trader submits EOD curves

- Futures curve
    
- Basis curve
    
- Illiquid extensions
    
- Shaped points
    

---

### Step 2: IPV performs checks

Typical checks:

- **Tolerance checks**
    
    - Trader curve vs independent sources
        
- **Day-on-day moves**
    
- **Shape checks**
    
    - Kinks, jumps, seasonality breaks
        
- **Cross-commodity sanity**
    
    - Gas vs power vs oil linkages
        
- **Liquidity tagging**
    
    - Observable vs non-observable inputs (IFRS 13 / ASC 820)
        

---

### Step 3: Outcomes

1. **Approved as-is**
    
2. **Approved with adjustment**
    
3. **Challenged**
    
4. **Escalated**
    

---

## 5. What happens during a challenge ⚠️

This is where things get tense.

- Trader must:
    
    - Defend assumptions
        
    - Provide market evidence
        
- IPV may:
    
    - Override the curve
        
    - Apply conservative pricing
        
- If unresolved:
    
    - Escalation to:
        
        - Head of Trading
            
        - Head of Risk
            
        - Valuation Committee
            

Final decision is:

> **Risk-adjusted, not trader-optimal**

---

## 6. Governance committees (real power structure)

Serious firms run:

- **Valuation Committee**
    
- **Model Risk Committee**
    

They:

- Approve:
    
    - New curve methodologies
        
    - New basis models
        
    - Changes in shaping logic
        
- Review:
    
    - Large PnL swings
        
    - Model vs realization gaps
        
- Set:
    
    - Tolerances
        
    - Escalation thresholds
        

---

## 7. Observable vs non-observable curves (huge deal)

Accounting rules require:

- Clear classification:
    
    - Level 1: exchange-traded
        
    - Level 2: broker / observable
        
    - Level 3: trader judgement
        

Basis curves often fall into **Level 3**.

Consequences:

- PnL reserves
    
- Valuation adjustments (VA)
    
- Capital charges
    
- Audit scrutiny
    

This is why IPV is not optional.

---

## 8. How firms reduce trader dominance risk

Common controls:

- Rotation of curve ownership
    
- Mandatory documentation
    
- Dual sign-off
    
- Independent curve construction
    
- Forced conservative marks in illiquid markets
    

Still:

> No system fully eliminates key-person risk — only reduces it.

---

## 9. Endur / ETRM implementation reality

In Endur-like systems:

- Traders:
    
    - Propose curves in sandbox
        
- Risk/IPV:
    
    - Promote curves to official environment
        
- System enforces:
    
    - Role-based access
        
    - Audit trails
        
    - Versioning
        
    - Approval workflows
        

If an ETRM lets traders directly control valuation curves:

> 🚨 **That firm is one audit away from a disaster**

---

## 10. Bottom line (the truth)

- Yes, **there is a separate independent team**
    
- Curve governance is:
    
    - A control function
        
    - A profit protection mechanism
        
- Traders create edge
    
- Risk validates reality
    

Or in one sentence:

> **Traders create beliefs. Risk enforces truth. Finance records consequences.**