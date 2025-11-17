# 🛢️ Oil Swaps & Futures: An Obsidian Note

## 🗂️ Overview

This note covers everything you need to know about **oil price swaps**, how their cash flows can be replicated using **futures contracts** (sometimes called "synthetic swaps" or swap replication), and how to hedge swap positions using futures. Each section builds from the fundamentals to more advanced mechanics, with lots of clarity, actionable takeaways—and some emoji flair for visual appeal! 🎯

## ⚡ 1. Oil Price Swaps: The Basics

- **What is an Oil Swap?**  
    An agreement where one party exchanges a series of fixed payments (fixed price per barrel) for floating payments (market price per barrel) over time.
    
    - 🔹 **Oil producer:** Wants to lock in a fixed price for sales (reducing risk).
        
    - 🔸 **Swap provider (bank):** Takes the opposite side.
        
- **Use case:**  
    Producers want predictable revenue, so they “sell” their floating market risk and “buy” a fixed price cash flow.
    

## 🔁 2. Replicating Swaps Using Futures Contracts

## 🎲 **Theory**

- In financial theory, holding a **portfolio of futures contracts** can create the same cash flow structure as a swap.
    
- **Arbitrage** ensures swap prices mirror the equivalent portfolio of futures (or forwards).
    

## 🟢 **How to Build a Synthetic Swap with Futures**

- **Fixed Leg:**  
    _Sell_ (short) enough futures contracts to match each delivery month’s oil volume.
    
- **Floating Leg:**  
    Gradually _buy back_ the contracts ("unwind" your short) daily throughout each month to mirror floating price exposure (mimicking physical sales at spot).
    

## Example:

> 1,000 barrels/day for all of 1998  
> For January:
> 
> - 20 trading days
>     
> - "Nearby" Feb contract trades for first 12 days, March contract for last 8 days
>     
> - Sell: 12/20 × 31 = **18.6 Feb contracts**
>     
> - Sell: 8/20 × 31 = **12.4 Mar contracts**
>     
> - Adjust for all months, across the year
>     

## ⏳ 3. Why **Discounting** Matters

- **Payment schedules for swaps** vs. **futures margining** differ.
    
    - Swaps: Often quarterly settlements.
        
    - Futures: Marked-to-market daily.
        
- Calculate the **present value** (PV) of hedge positions:  
    Use the discount factor
    
    DF=e−r⋅tDF=e−r⋅t
    
    _(r = interest rate, t = time fraction)_
    

## 📊 4. Weighted Average Price

- For each quarter:  
    Multiply discounted contracts by respective futures prices to get a **weighted average** price for the period.
    

> Example (Q1):
> 
> Avg=(19×20.99)+(32×20.90)+(27×20.81)+(10×20.72)88=$20.87/bblAvg=88(19×20.99)+(32×20.90)+(27×20.81)+(10×20.72)=$20.87/bbl

- Do this for all quarters, then average for the year.
    

## 🚦 5. Day-to-Day Mechanics

- Sell your portfolio of short futures—**locks in your fixed price**.
    
- Each day you sell real oil (physically), **buy back a portion** of the outstanding futures—mirrors "floating" market exposure.
    
- Final result: Combination of real sales + net P&L from futures = **fixed “swap” price** for the year.
    

## 🧮 6. Hedging a Swap Exposure with Futures

## 💡 **Key Insight**

- If you _already hold_ a swap, you hedge your risk by taking a **futures position in the opposite direction** of your cash flow exposure.
    

## **Mapping Swap ↔️ Futures Hedge**

|Swap Position|Receive/Pay|Risk from Price Moves|Hedge with...|
|---|---|---|---|
|**Long swap**|Receive fixed, pay floating|Prices fall (swap loses)|Short futures|
|**Short swap**|Pay fixed, receive floating|Prices rise (swap loses)|Long futures|

## **Example:**

- **Short swap** (pay $60 fixed, receive floating). If oil rises to $70:
    
    - Lose $10 in swap (pay more than receive).
        
    - Win $10 in long futures (as price rises).
        
    - Net = 0 (offsetting positions).
        

## 🧲 7. Big Picture Table

|Perspective|What They Want|How to Replicate with Futures|How to Hedge Swap Risk|
|---|---|---|---|
|Producer|Lock fixed price|Sell (short) futures portfolio|N/A (already synthetic swap)|
|Swap Provider|Float exposure|Buy (long) futures portfolio|Take _opposite_ futures position|

## 📝 8. Key Takeaways

- 🌟 **Replicating swaps** with futures lets you match swap cash flows without an actual swap contract.
    
- 🌟 **Hedging swap positions** with futures means holding the _opposite_ position in futures to your swap risk.
    
- 🌟 This relationship is why swaps, forwards, and futures prices are tightly linked by arbitrage.
    

## 💬 9. Visual Concept: Emoji Cheat Sheet

- 🔻**Short Swap** (pay fixed, receive float): Hedge with 🔼 **Long Futures**
    
- 🔺**Long Swap** (receive fixed, pay float): Hedge with 🔽 **Short Futures**
    
- 🛡️ **Purpose:** Use futures as a shield to neutralize swap risk!
    

## 💡 10. Final Thoughts

- Every step in swap replication or hedging boils down to **matching your desired price exposure**—using swaps, futures, or both.
    
- **Careful portfolio management, timing, and present value math** ensure perfect hedging and risk transfer.