We are given `n` cities numbered from `0` to `n-1`, and a list of flights where each flight is defined as `[from, to, cost]`. We need to find the cheapest price from `src` to `dst` using at most `k` stops.

---

## ✍️ My Initial Approach (Priority Queue + Greedy)

### 🔍 Code:

```cpp
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        vector<vector<pair<int,int>>> graph(n);
        for(auto it: flights){
            graph[it[0]].push_back({it[1],it[2]});
        }

        priority_queue<tuple<int,int,int>, vector<tuple<int,int,int>>, greater<>> pq;
        pq.push({0, 0, src});  // {cost, stops, node}
        int dist = INT_MAX;

        while(!pq.empty()) {
            auto [currDist, currMoves, currNode] = pq.top();
            pq.pop();

            if(currNode == dst)
                dist = min(dist, currDist);
            if(currMoves >= k) continue;

            for(auto& it : graph[currNode]) {
                if (currDist + it.second < dist)
                    pq.push({currDist + it.second, currMoves + 1, it.first});
            }
        }

        return dist == INT_MAX ? -1 : dist;
    }
};

```
### ❌ Mistakes:

- **Restrictive Pruning**: The condition `currDist + it.second < dist` prevents exploring valid paths that might initially be costlier but result in cheaper routes later.
    
- **Incorrect Termination**: Greedy assumption that the first time we hit `dst`, it's the best path — only true for Dijkstra **without stop limits**.
    
- **No Per-Stop Tracking**: Fails to handle cases where same node is reached with different number of stops.
    

---

## ✅ My Second Approach (BFS, No Priority Queue)

### 🔍 Code:

```cpp
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        vector<vector<pair<int,int>>> g(n);
        for(auto& i : flights) g[i[0]].push_back({i[1], i[2]});
        
        vector<int> dist(n, INT_MAX);
        dist[src] = 0;
        queue<pair<int, int>> q;  // {cost, node}
        q.push({0, src});
        k += 1; // account for number of edges (not stops)

        while(!q.empty() && k--) {
            int sz = q.size();
            vector<int> temp = dist;  // only update after this level

            while(sz--) {
                auto [d, s] = q.front(); q.pop();
                for(auto& [nei, cost] : g[s]) {
                    if(temp[nei] > d + cost) {
                        temp[nei] = d + cost;
                        q.push({temp[nei], nei});
                    }
                }
            }
            dist = temp;
        }

        return dist[dst] == INT_MAX ? -1 : dist[dst];
    }
};

```
### ✅ What This Got Right:

- BFS level order traversal where each level = one more stop.
    
- Uses a temp vector per level to avoid propagating same-level updates.
    
- Avoids revisiting worse paths early.
    

### ⚠️ But Still Risky:

- **1D `dist[]` too coarse**: Can miss cheaper paths that arrive at same node but at a later level (i.e., with more stops).
    
- Passes most cases, but not theoretically sound for all inputs.
    

---

## ✅ Final Correct Approach: BFS with (Node, Stop)-Level Dist Tracking

### 🔍 Code:

```cpp
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        vector<vector<pair<int, int>>> graph(n);
        for (auto& f : flights) {
            graph[f[0]].emplace_back(f[1], f[2]);
        }

        vector<vector<int>> dist(n, vector<int>(k + 2, INT_MAX));
        dist[src][0] = 0;

        queue<tuple<int, int, int>> q;  // {node, cost, stops}
        q.push({src, 0, 0});

        while (!q.empty()) {
            auto [node, cost, stops] = q.front(); q.pop();
            if (stops > k) continue;

            for (auto& [nei, price] : graph[node]) {
                int newCost = cost + price;
                if (newCost < dist[nei][stops + 1]) {
                    dist[nei][stops + 1] = newCost;
                    q.push({nei, newCost, stops + 1});
                }
            }
        }

        int ans = *min_element(dist[dst].begin(), dist[dst].end());
        return ans == INT_MAX ? -1 : ans;
    }
};

```
### ✅ Why This Works:

- Tracks cheapest cost to reach each node **at each stop count**.
    
- Prunes only if we’ve already reached the node with a cheaper cost at that exact stop level.
    
- Ensures that **cheaper paths with more stops aren't missed**, unlike 1D `dist[]`.
    

---

## 🧠 Takeaways

- If there's a constraint on "number of stops", always track cost per `(node, stop_count)` — not just per node.
    
- Greedy is not always safe in constrained shortest path problems.
    
- BFS is preferable when all edge weights are uniform or when we care about levels (like stops).
    
- Dijkstra (min-heap) is preferable when we care about cost and want early pruning — **but only when no constraint on number of stops**.