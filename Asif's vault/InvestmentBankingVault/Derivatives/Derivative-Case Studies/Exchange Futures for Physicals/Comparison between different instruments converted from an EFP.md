
📘 Core Idea  
An EFP (Exchange of Futures for Physical) is a bundled position consisting of:

🔹 Physical Index Gas (you receive physical gas priced at index)  
🔹 Short Futures Position (via transfer of futures at posted price)  
🔹 Basis Swap (the EFP differential, i.e., Index – Futures)

Because of this modularity, an EFP can be **converted** into various instruments by stripping out one or more components.

---

📦 EFP Components Recap (for the Buyer)

🔸 Physical Gas: ✅ Long  
🔸 Basis Swap (differential): ✅ Long  
🔸 Futures Position: ❌ Short

---

🔁 Conversion Paths

1️⃣ Convert EFP into 📈 Physical Index Gas

- Actions:  
    🔹 Sell the basis swap (offset the differential)  
    🔹 Buy back the short futures
    
- Result: ✅ Long Index Gas
    
- Effective Price: Index
    
- Use Case: You want exposure to floating gas price without fixed or basis components.
    

---

2️⃣ Convert EFP into 🔒 Fixed-Price Physical Gas

- Actions:  
    🔹 Buy back short futures  
    ❌ Leave basis component untouched
    
- Result: ✅ Long Physical Gas at Fixed Price
    
- Effective Price: Futures Buyback Price + EFP Differential
    
- Use Case: You want to receive physical gas and fix the all-in purchase price.
    

---

3️⃣ Convert EFP into 🔀 Basis Swap

- Actions:  
    🔹 Sell physical gas at index  
    🔹 Buy back short futures
    
- Result: ✅ Long Basis Swap (Index – Futures)
    
- Effective Basis: EFP Differential
    
- Use Case: You want to trade or hedge location basis (e.g., Permian – Henry Hub).
    

---

4️⃣ Convert EFP into 🔁 Futures Swap

- Actions:  
    🔹 Sell physical gas at index  
    🔹 Sell basis swap (offset basis exposure)  
    ❌ Keep futures position (remain short)
    
- Result: ✅ Short Futures Exposure
    
- Use Case: You want to speculate or hedge Henry Hub prices independently of basis or physical gas.
    

---

5️⃣ Convert EFP into 🔃 Index Swap (Fixed-for-Float)

- Actions:  
    🔹 Sell physical gas  
    🔹 Offset basis swap  
    🔹 Offset futures  
    🔹 Add a new fixed leg (via financial swap)
    
- Result: ✅ Financial Index Swap (Pay Fixed, Receive Index)
    
- Use Case: You want to create or hedge a fixed-vs-floating (index) financial exposure.
    

---

📊 Summary Comparison Table

|Conversion Target|🔁 Strip Futures|🔄 Strip Basis|📦 Strip Physical|🎯 Result|📌 Use Case|
|---|---|---|---|---|---|
|📈 Index Gas|✅ Yes|✅ Yes|❌ No|Physical Index Gas|Hold floating index exposure|
|🔒 Fixed-Price Gas|✅ Yes|❌ No|❌ No|Fixed-Price Physical Gas|Lock in all-in fixed cost for delivery|
|🔀 Basis Swap|✅ Yes|❌ No|✅ Yes|Long Basis Swap|Express or hedge basis risk|
|🔁 Futures Swap|❌ No|✅ Yes|✅ Yes|Short Futures Exposure|Isolate Henry Hub risk|
|🔃 Index Swap|✅ Yes|✅ Yes|✅ Yes|Financial Fixed-to-Float Swap|Create or hedge fixed vs index swap|

---

🧠 Key Takeaways

- EFPs are flexible by design — you can peel off any leg (futures, basis, or index gas) to match your strategy.
    
- Each conversion lets you **reshape** your exposure without needing a new transaction.
    
- The EFP differential represents your locked-in **basis value**.
    
- You gain **pricing control** via the futures leg and **location flexibility** via the basis differential.



[[Converting EFP to Basis Swaps]]
[[Converting EFP to Fixed-Priced Physical Gas]]
[[Converting EFP to Index-Priced physical gas]]
[[Exchange futures for physical- Key points]]
[[Exchange of futures for physical gas]]
[[Basis Swaps.md]]
[[Commodity Futures.md]]
[[Converting EFP to Futures Swap]]

