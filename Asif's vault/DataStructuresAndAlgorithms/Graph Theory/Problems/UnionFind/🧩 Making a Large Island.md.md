### 🔗 Problem

Leetcode Problem: **Making a Large Island**

Goal: Given a grid of 0s and 1s, change at most one `0` to `1` such that the largest island (connected group of 1s) is maximized. Return the size of that island.

---

### 🧠 Approach (My Idea)

- First, identify all clusters (connected `1`s) using **DFS/BFS** and label each with a **unique color (integer > 1)**.
    
- While labeling, maintain a mapping from cluster color to **cluster size** using `unordered_map<int, int>`.
    
- Second pass: For every cell with `0`, check its 4 neighbors.
    
    - Collect unique neighboring cluster colors.
        
    - Sum up their sizes, and add `1` (for this flipped 0).
        
    - Track the **maximum** such value.
        

---

### ⚙️ Final Accepted Code

```cpp
class Solution {
public:
    bool is_valid(int x, int y, int n) {
        return x >= 0 && x < n && y >= 0 && y < n;
    }

    void dfs(vector<vector<int>>& grid, int color, unordered_map<int,int> &clusterSize, int x, int y){
        grid[x][y] = color;
        clusterSize[color]++;
        vector<int> dir = {0, 1, 0, -1, 0};
        for(int i = 0; i < 4; i++){
            int dx = x + dir[i];
            int dy = y + dir[i + 1];
            if(is_valid(dx, dy, grid.size()) && grid[dx][dy] == 1)
                dfs(grid, color, clusterSize, dx, dy);
        }
    }

    int largestIsland(vector<vector<int>>& grid) {
        int n = grid.size();
        unordered_map<int,int> clusterSize;
        int currentColor = 2, zeroCount = 0;

        // First pass: DFS to color and record sizes
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                if(grid[i][j] == 1){
                    dfs(grid, currentColor, clusterSize, i, j);
                    currentColor++;
                } else if(grid[i][j] == 0)
                    zeroCount++;
            }
        }

        if(zeroCount == 0)
            return n * n;

        int ans = 0;
        vector<int> dir = {0, 1, 0, -1, 0};

        // Second pass: Try flipping each 0 and calculate resulting island size
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                if(grid[i][j] == 0){
                    int currentClusterSize = 0;
                    unordered_set<int> seenColors;

                    for(int k = 0; k < 4; k++){
                        int dx = i + dir[k];
                        int dy = j + dir[k + 1];
                        if(is_valid(dx, dy, n) && grid[dx][dy] > 1 && seenColors.find(grid[dx][dy]) == seenColors.end()){
                            currentClusterSize += clusterSize[grid[dx][dy]];
                            seenColors.insert(grid[dx][dy]);
                        }
                    }

                    ans = max(ans, currentClusterSize + 1);
                }
            }
        }

        return ans;
    }
};
```

---

### 🧼 Common Mistake Debugged

**Bug**: `dir[i]` was mistakenly used instead of `dir[k]` inside direction loop:

cpp

CopyEdit

`int dx = i + dir[i];   // ❌ Wrong int dy = j + dir[i+1]; // ❌ Wrong`

✅ Fix:

cpp

CopyEdit

`int dx = i + dir[k]; int dy = j + dir[k+1];`

Also, `ans = max(...)` should be **outside the direction loop**.

---

### ✅ Review

|Category|Rating|Comments|
|---|---|---|
|Correctness|✅ 10/10|Passes all edge cases and is logically sound|
|Time Complexity|⚡ 8.5/10|O(N²) — optimal for this problem|
|Space Complexity|💾 8.5/10|Acceptable, could use vector instead of map|
|Readability|🧼 8/10|Clean and modular; naming can improve|
|Optimization Potential|🧠 7.5/10|DFS→BFS or map→vector switch possible|

---

### 🧠 Ideas for Optimization

- Use `vector<int>` for `clusterSize` if cluster IDs are compact.
    
- Switch to **BFS** for large grid safety (avoid stack overflow).
    
- Skip processing of 0s completely surrounded by 0s.