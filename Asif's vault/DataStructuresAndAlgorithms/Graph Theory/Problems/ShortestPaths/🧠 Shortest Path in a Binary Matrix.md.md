### 📌 Problem Summary

Given an `n x n` binary matrix `grid`:

- `0` represents an **open cell**
    
- `1` represents a **blocked cell**
    

We must find the **shortest path from** `(0, 0)` **to** `(n - 1, n - 1)`:

- Movement allowed in **8 directions** (horizontal, vertical, diagonal).
    
- Return the **number of steps in the shortest path**, or `-1` if no such path exists.
    

---

### ❓ Initial Question

> "Should I only check cells that are below or to the right of me (i.e., toward the goal), or all 8 directions?"

#### ✅ Answer:

**You must check all 8 directions**.

Even though the goal is in the bottom-right corner, shortest paths may require navigating **around obstacles**, which means:

- You might need to move **up** or **left** temporarily.
    
- Restricting movement to "toward the goal" might miss valid shorter paths.
    

---

### 🔁 BFS Approach

**Why BFS?**

- BFS naturally finds the shortest path in an unweighted graph (which is what this grid is).
    

**8-directional movement**:

cpp

CopyEdit

`vector<pair<int, int>> directions = {     {1, 0}, {0, 1}, {-1, 0}, {0, -1},     {1, 1}, {-1, -1}, {1, -1}, {-1, 1} };`

---

### 💡 C++ Implementation

```cpp
#include <vector>
#include <queue>
using namespace std;

int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
    int n = grid.size();
    if (grid[0][0] != 0 || grid[n - 1][n - 1] != 0) return -1;

    vector<pair<int, int>> directions = {
        {1, 0}, {0, 1}, {-1, 0}, {0, -1},
        {1, 1}, {-1, -1}, {1, -1}, {-1, 1}
    };

    queue<pair<int, int>> q;
    q.push({0, 0});
    grid[0][0] = 1;  // Mark starting cell with distance

    while (!q.empty()) {
        auto [x, y] = q.front();
        q.pop();
        int dist = grid[x][y];

        if (x == n - 1 && y == n - 1) return dist;

        for (auto [dx, dy] : directions) {
            int nx = x + dx, ny = y + dy;
            if (nx >= 0 && ny >= 0 && nx < n && ny < n && grid[nx][ny] == 0) {
                q.push({nx, ny});
                grid[nx][ny] = dist + 1;
            }
        }
    }

    return -1;  // No valid path found
}
```

---

### 🧠 Key Takeaways

- Always check all 8 directions when diagonals are allowed.
    
- Use BFS for shortest path in unweighted grids.
    
- You can reuse the input grid to track visited cells and distances.
    
- Avoid premature pruning based on direction bias.