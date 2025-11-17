# Avg Proj By Leg Result

## Overview

The **Avg Proj By Leg Result** shows the average projected price by leg in a transaction.  
It reflects the **day-weighted average price** for all past resets of a profile record.

## Attributes

- **Result ID:** 118
    
- **Result Enumeration:** `AVG_PROJ_BY_LEG_RESULT`
    
- **Result Class:** Tran Result
    

## Toolsets

- ComOptFut
    
- Commodity
    
- EngyLTP
    
- ComOpt
    
- ComSwap
    
- EngyTS
    
- MetalOpt
    
- MetalSwap
    
- Power
    

## Description

Captures the **average price across all past resets** for a given trade leg.  
Uses **day-weighting methodology** to properly scale the average based on reset periods.  
Useful for measuring the effective traded price realized so far on instruments with multiple reset periods (e.g., swaps, futures, and options).

---

## Worked Example: Day-Weighted Average Price

Suppose a transaction leg has three past resets:

|Reset Period|Days|Reset Price|
|---|---|---|
|Period 1|10|95.00|
|Period 2|5|100.00|
|Period 3|15|105.00|

**Calculation Steps:**

1. Calculate the sum of (reset price × days in period) for all resets:
    
    - Period 1: 95.00×10=950.0095.00×10=950.00
        
    - Period 2: 100.00×5=500.00100.00×5=500.00
        
    - Period 3: 105.00×15=1575.00105.00×15=1575.00
        
2. Add the period totals: 950.00+500.00+1575.00=3025.00950.00+500.00+1575.00=3025.00
    
3. Calculate the total number of days: 10+5+15=3010+5+15=30
    
4. Compute the day-weighted average: 3025.0030=100.83303025.00=100.83
    

So, the **Avg Proj By Leg Result** for these resets is **100.83**.

---

## Usage Context

This calculation gives Endur users the actual time-weighted realized price for trades with multiple resets.  
It is critical for evaluating mark-to-market, accruals, and P&L calculations on swaps, futures, and options where past resets define realized price.

---

Copy and paste this note into Obsidian to enhance your reference collection for Endur results and commodity risk workflows.