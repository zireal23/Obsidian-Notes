
### 🧠 Intuition

  

This problem involves removing the maximum number of stones such that at least one stone remains in each connected component. Two stones are considered connected if they share the same row or column.

  

**Key Insight**:  

We can use **Disjoint Set Union (DSU)** to group stones into components. However, since stones are given as `(x, y)` coordinates and DSU operates on 1D sets, we can model a stone by connecting its `x` and `y` coordinate using DSU.

  

To avoid coordinate overlap, we offset the `y` coordinate by a fixed amount (greater than max x). This turns a 2D coordinate into two unique 1D nodes.

  

### Example:

- Stone at `(1, 3)` → connect node `1` and node `3 + offset`.

- Connecting all such pairs groups stones that share rows or columns into a single component.

  

Once all unions are made, the number of **connected components** gives the number of stones that **must remain**, and we can remove the rest.

  

### 🐞 Bug & Debugging Insight

  

#### What went wrong:

Initially, we counted the number of components by iterating through all **stones** and checking if either their row or column coordinate was its **own parent**.

  

However, this incorrectly overcounted components. For example, in a component of 6 stones (like all in the same row), each node could still report itself as a root **because they were never merged on that specific node**, leading to **6 components counted instead of 1**.

  

#### Fix:

We should iterate through **all the unique nodes (both x and offset y)** and count only those where `parent[node] == node`. That way, each distinct component is counted exactly once.

  

This fixes the overcounting issue and gives the correct number of components.

  
  

## ✅ Final Code

  

```cpp

class DisjointSetUnion {

private:

    vector<int> parent;

    vector<int> size;

  

public:

    DisjointSetUnion(int n) {

        parent.resize(n);

        size.resize(n, 1);

        for (int i = 0; i < n; i++) parent[i] = i;

    }

  

    int find(int x) {

        if (parent[x] != x) {

            parent[x] = find(parent[x]); // Path compression

        }

        return parent[x];

    }

  

    void unionSets(int x, int y) {

        int px = find(x);

        int py = find(y);

        if (px == py) return;

  

        if (size[px] < size[py]) {

            parent[px] = py;

            size[py] += size[px];

        } else {

            parent[py] = px;

            size[px] += size[py];

        }

    }

};

  

class Solution {

public:

    int removeStones(vector<vector<int>>& stones) {

        int maxX = 0, maxY = 0;

        for (auto& s : stones) {

            maxX = max(maxX, s[0]);

            maxY = max(maxY, s[1]);

        }

  

        int offset = maxX + 1; // offset y values to avoid collision with x

        DisjointSetUnion dsu(maxX + maxY + 2);

        unordered_set<int> seen;

  

        for (auto& s : stones) {

            int row = s[0];

            int col = s[1] + offset;

            dsu.unionSets(row, col);

            seen.insert(row);

            seen.insert(col);

        }

  

        int components = 0;

        for (int node : seen) {

            if (dsu.find(node) == node) {

                components++;

            }

        }

  

        return stones.size() - components;

    }

};

```

  

## ⚠️ Common Mistakes

  

1. **Overcounting Components**:  

   The biggest issue can be overcounting when checking the connected components. If you treat both the row and column as separate nodes and count them as individual components, you may count too many. To avoid this, ensure that you only count unique components formed by the **union** of the row and column.

  

2. **Incorrect Mapping of Coordinates**:  

   When modeling the stone as two nodes (for the x and y coordinates), make sure that you correctly offset the `y` coordinate by adding a constant value (greater than max `x`) to avoid clashes between `x` and `y` indices in the DSU.

  

3. **Misunderstanding Union-Find Operations**:  

   Remember that when using union-find (DSU), you need both **union** and **find** operations. The `find` operation needs to employ **path compression** to ensure that each stone node is pointing directly to its representative (root), speeding up future operations.

  

4. **Boundary Issues with Array Size**:  

   Ensure that the array used for DSU operations is large enough to accommodate both the `x` and `y` coordinate values (consider the maximum possible values). Also, ensure that you don’t exceed the array bounds when assigning values.