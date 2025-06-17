### 📌 Problem Summary

You're given a 2D grid `heights`, where each cell represents an elevation.

**Goal**: Find a path from **(0,0)** to **(m-1,n-1)** minimizing the **maximum effort** required between any two consecutive cells along the path.

- Movement allowed: **up, down, left, right**
    
- **Effort** between two cells: `abs(height1 - height2)`
    
- **Path effort**: maximum of all such efforts along the path
    

---

### 💡 Key Insight

This is **not** a classic shortest path where we sum edge weights.  
Instead, the **cost of a path is defined by the single worst step**.

So, we use a **modified Dijkstra**:

- Each state tracks the **maximum effort so far**.
    
- At each neighbor, compute:  
    `newEffort = max(currentEffort, abs(height[x][y] - height[nx][ny]))`
    

---

### ✅ C++ Implementation

```cpp
#include <vector>
#include <queue>
#include <cmath>
using namespace std;

int minimumEffortPath(vector<vector<int>>& heights) {
    int m = heights.size(), n = heights[0].size();
    vector<vector<int>> dist(m, vector<int>(n, INT_MAX));
    dist[0][0] = 0;

    priority_queue<tuple<int, int, int>, vector<tuple<int, int, int>>, greater<>> pq;
    pq.emplace(0, 0, 0);

    vector<pair<int, int>> directions = {
        {1, 0}, {-1, 0}, {0, 1}, {0, -1}
    };

    while (!pq.empty()) {
        auto [effort, x, y] = pq.top(); pq.pop();
        if (x == m - 1 && y == n - 1) return effort;

        for (auto [dx, dy] : directions) {
            int nx = x + dx, ny = y + dy;
            if (nx >= 0 && ny >= 0 && nx < m && ny < n) {
                int diff = abs(heights[x][y] - heights[nx][ny]);
                int newEffort = max(effort, diff);
                if (newEffort < dist[nx][ny]) {
                    dist[nx][ny] = newEffort;
                    pq.emplace(newEffort, nx, ny);
                }
            }
        }
    }

    return 0; // Unreachable
}

```

---

### 🤔 Why `max(effort, diff)`?

Because we want to **minimize the largest jump** along the path:

- `effort`: Max effort **seen so far**.
    
- `diff`: Effort to the **next cell**.
    
- `newEffort`: Worst effort if we take this next cell.
    

This lets Dijkstra always pick the “least painful” path at every step.

---

### 📊 Time & Space Complexity

- **Time**: `O(m * n * log(mn))` — Each cell may be pushed into the priority queue once.
    
- **Space**: `O(m * n)` for the distance matrix and priority queue.
    

---

### 🧠 Summary

- Track maximum effort instead of summing edge weights.
    
- Dijkstra works even when edge cost is dynamic (in this case, the height difference).
    
- Priority queue ensures we always explore the most promising path.