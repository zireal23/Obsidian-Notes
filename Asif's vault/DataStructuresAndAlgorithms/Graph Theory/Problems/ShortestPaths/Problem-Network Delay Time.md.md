Given a directed weighted graph of `n` nodes (labeled from `1` to `n`), and a list of travel times as directed edges `times[i] = (u, v, w)`, where `u` is the source node, `v` is the target node, and `w` is the time it takes for a signal to travel from `u` to `v`.

We send a signal from a starting node `k`. The goal is to find the time it takes for all the `n` nodes to receive the signal. If it is impossible, return `-1`.

---

## My Question:

> According to this logic, the very first time that we reach a node will always have the lowest weighted path?

### Answer:

Yes. In Dijkstra's algorithm with a min-heap (priority queue), the first time a node is popped from the priority queue, the shortest (lowest weighted) path to that node has been found, assuming:

- All edge weights are non-negative (a requirement for Dijkstra's algorithm)
    
- The graph is static (edges and weights don't change during execution)
    

This is why a `visited` array can be used to avoid reprocessing nodes unnecessarily.

---

## Initial Implementation:

```cpp
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<int> nodeTimes(n+10,INT_MAX);
        vector<vector<pair<int,int>>> graph(n+10);
        for(auto it: times)
            graph[it[0]].push_back({it[1],it[2]});

        priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq;
        pq.push({0,k});
        nodeTimes[k] = 0;
        while(!pq.empty()){
            auto curr = pq.top();
            pq.pop();
            for(auto it: graph[curr.second])
                if(it.second+curr.first<nodeTimes[it.first]){
                    nodeTimes[it.first] = it.second+curr.first;
                    pq.push({nodeTimes[it.first],it.first});
                }
        }
        int ans = INT_MIN;
        for(int i=1;i<=n;i++){  // BUG: should be i <= n
            if(nodeTimes[i]==INT_MAX)
                return -1;
            ans = max(ans,nodeTimes[i]);    
        }

        return ans;
    }
};
```

### Bug Fix:

Change `for(int i = 1; i < n; i++)` to `for(int i = 1; i <= n; i++)`

---

## Optimized Implementation (with visited set):

```cpp
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<int> nodeTimes(n + 1, INT_MAX);
        vector<vector<pair<int, int>>> graph(n + 1);
        vector<bool> visited(n + 1, false);

        for (auto& it : times) {
            graph[it[0]].push_back({it[1], it[2]});
        }

        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<>> pq;
        pq.push({0, k});
        nodeTimes[k] = 0;

        while (!pq.empty()) {
            auto [currTime, node] = pq.top();
            pq.pop();

            if (visited[node]) continue;
            visited[node] = true;

            for (auto& [nei, time] : graph[node]) {
                if (!visited[nei] && currTime + time < nodeTimes[nei]) {
                    nodeTimes[nei] = currTime + time;
                    pq.push({nodeTimes[nei], nei});
                }
            }
        }

        int ans = 0;
        for (int i = 1; i <= n; ++i) {
            if (nodeTimes[i] == INT_MAX) return -1;
            ans = max(ans, nodeTimes[i]);
        }

        return ans;
    }
};
```