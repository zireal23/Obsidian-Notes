# 🌲 Greedy Method for MST

The **greedy method** is a general paradigm for constructing a **Minimum Spanning Tree (MST)** in a connected, undirected graph with positive edge weights.

---

## 📌 Key Idea
Build the MST **incrementally**, choosing at each step the **minimum weight edge** that doesn’t form a cycle (i.e., maintains tree property).

---

## ✅ Properties
- **Greedy Choice Property:** Always pick the minimum weight valid edge.
- **Optimal Substructure:** A subset of the MST is itself an MST of the subset of vertices.
- **Correctness:** Guaranteed by the [[Cut Property]].

---

## 🛠️ General Algorithm
1. Start with all edges colored **gray**.
2. Find any [[Cut]] in the graph that has **no black (selected) crossing edges**.
3. Color the **minimum weight crossing edge** **black** (add to MST).
4. Repeat until exactly **V - 1 edges** are black (V = number of vertices).

---

## 🧠 Simplifying Assumptions
- **Distinct edge weights** → Ensures MST is **unique**.
- **Graph is connected** → Otherwise, we get a **minimum spanning forest**.

---

## ⚠️ Non-Distinct Weights
- MST might not be unique.
- Algorithm still correct, but **proof of correctness** is more complex.

---

## 🧪 Implementations
Greedy method can be specialized in different ways:
- [[Kruskal's Algorithm]]
- [[Prim's Algorithm]]
- Borůvka’s Algorithm (less common, hybrid of Kruskal and Prim)

---

## 📚 Related Concepts
- [[MST]]
- [[Cut Property]]
- [[Crossing Edge]]
- [[Cycle Detection]]
- [[Union Find]]
- [[Priority Queue]]

---

## 🧾 Notes
- Greedy approach ensures **locally optimal choices lead to globally optimal result**.
- Edge selection based on **cut-safety** and **no cycle creation**.

