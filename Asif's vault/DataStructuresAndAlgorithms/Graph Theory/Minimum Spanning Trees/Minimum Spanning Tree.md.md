# Minimum Spanning Tree (MST)

**Definition:**  
A spanning tree of a connected, undirected graph G with positive edge weights is a subgraph T that is **connected, acyclic (a tree), and spanning (includes all vertices)**.

**Goal:**  
Find a spanning tree with the **minimum total edge weight**.

**Importance:**  
MST is a fundamental problem with diverse applications.

**Applications:**
- Network design (communication, electrical, hydraulic, computer, road)
- Clustering analysis
- Max bottleneck paths
- Real-time face verification
- LDPC codes for error correction
- Image registration with Renyi entropy
- Finding road networks in satellite and aerial imagery
- Reducing data storage in sequencing amino acids in a protein
- Model locality of particle interactions in turbulent fluid flows
- Autoconfig protocol for Ethernet bridging to avoid cycles
- Approximation algorithms for NP-hard problems (e.g., TSP, Steiner tree)
- Medical image processing (dithering)
- Models of nature (arrangement of nuclei)
- Bicycle routes
- Scientific applications (clustering of cancers)

---

## [[Greedy Algorithm MST]]

The greedy algorithm is a general approach for finding a Minimum Spanning Tree.  
It works by **iteratively adding the minimum weight edge** that satisfies a certain condition.  
The correctness of the greedy MST algorithm is based on the [[Cut Property]].

### General Steps
1. Start with all edges coloured gray.
2. Find any [[Cut]] in the graph that has **no black (already selected) crossing edges**.
3. Colour the **minimum weight crossing edge** of that cut black (add it to the MST).
4. Repeat until **V - 1 edges** are coloured black.

### Correctness
- Any edge coloured black by the greedy algorithm is guaranteed to be in the MST due to the [[Cut Property]].
- If fewer than V - 1 edges are black, there must exist a [[Cut]] with no black crossing edges.

### Simplifying Assumptions
- **Distinct Edge Weights:** Ensures the MST is unique.
- **Connected Graph:** Otherwise, algorithm computes a **minimum spanning forest**.

### Non-Distinct Weights
- MST might not be unique.
- Greedy algorithm is still correct, but proof is more involved.

### Implementations
- [[Kruskal's Algorithm]]
- [[Prim's Algorithm]]
- Borüvka’s algorithm (brief mention)

---

## [[Cut Property]]

**Definition of a Cut:**  
A partition of vertices into two non-empty sets.

**Crossing Edge:**  
An edge with one endpoint in each set.

**Property:**  
In any [[Cut]], the **minimum weight crossing edge** is in the MST.  
If multiple edges have the same minimum weight, *some* such edge will be in *some* MST.

### Proof Sketch (by contradiction)
1. Assume the min crossing edge *e* is not in the MST.
2. Adding *e* creates a cycle.
3. The cycle must contain another crossing edge *f*.
4. Remove *f* and add *e*: still a valid tree.
5. Since *e* < *f*, the new tree has lower weight — contradiction.

---

## [[Cut]]

A **cut** is a partition of the graph's vertices into two non-empty subsets.

---

## [[Crossing Edge]]

An edge that connects one vertex from each subset of a [[Cut]].

---

## [[Kruskal's Algorithm]]

A specific [[Greedy Algorithm MST]] implementation.

### Steps:
1. Sort all edges by increasing weight.
2. Add the next edge if it **doesn’t form a cycle**.
3. Repeat until **V - 1** edges added.

### Cycle Detection:
Use [[Union-Find]] data structure.

### Efficiency:
- Sorting edges: **O(E log E)**
- If edges pre-sorted: **O(E log\* V)**

---

## [[Prim's Algorithm]]

Another [[Greedy Algorithm MST]] implementation.

### Steps:
1. Start from any vertex (e.g. vertex 0).
2. Grow tree by adding **minimum weight edge** with exactly one endpoint in tree.
3. Stop when tree has **V - 1 edges**.

### Implementations:

#### Lazy Prim's:
- Use priority queue of **edges**.
- May include redundant edges.
- Time: **O(E log E)**

#### Eager Prim's:
- Use indexed priority queue of **vertices**.
- Priority = weight of lightest edge connecting to tree.
- Time: **O(E log V)** (with binary heap)

---

## [[Union-Find]]

Used in [[Kruskal's Algorithm]] for cycle detection.

### Operations:
- `find(v)`: Find component containing vertex v.
- `union(u, v)`: Merge components of u and v.

---

## [[Priority Queue]]

Used in [[Prim's Algorithm]].

- Supports efficient min retrieval.
- Common implementations: binary heap, indexed priority queue.

---

## [[Cycle Detection]]

Used in [[Kruskal's Algorithm]] to check if adding an edge forms a cycle.  
Handled efficiently via [[Union-Find]].

