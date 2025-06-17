## Problem Overview

Given a list of accounts, where each account is represented by a name and a list of emails, the task is to merge accounts belonging to the same person. Two accounts belong to the same person if they share at least one common email.

## 🧠 Intuition

- All emails in a single account are definitely connected.
    
- If any email in one account is also present in another account, then the accounts are indirectly connected.
    
- Our goal is to find connected components of emails.
    

---

## 🧩 Approach 1: Union-Find (Disjoint Set)

### ✅ Intuition:

- Each email is a node in the union-find data structure.
    
- Emails belonging to the same account are unioned together.
    
- After union operations, find all root emails and group all emails belonging to the same root.
    

### 🧱 Union-Find Structure:

```
class DisjointSetString {
private:
    unordered_map<string, string> parent;
public:
    DisjointSetString() {}

    string find(const string& x){
        if(parent.find(x) == parent.end()){
            parent[x] = x;
        }
        if(parent[x] != x){
            parent[x] = find(parent[x]); // Path compression
        }
        return parent[x];
    }

    void unionSets(const string& x, const string& y){
        string xRoot = find(x);
        string yRoot = find(y);
        if(xRoot != yRoot){
            parent[yRoot] = xRoot;
        }
    }

    bool connected(const string& x, const string& y){
        return find(x) == find(y);
    }
};
```

### ❓ Doubt:

> Are we flattening the tree in the `find` function?

- Yes, the second `if` in `find` is path compression, which flattens the tree.
    

> Can this create skewed trees?

- Yes, which is why rank-based unioning is sometimes used. This solution skips it for simplicity.
    

---

## 🚀 Solution Code Using Union-Find

```
class Solution {
public:
    vector<vector<string>> accountsMerge(vector<vector<string>>& accounts) {
        unordered_map<string,string> email_name;
        DisjointSetString ds;

        // Union emails in the same account
        for(auto it: accounts){
            string name = it[0];
            email_name[it[1]] = name;
            for(int i = 2; i < it.size(); i++){
                ds.unionSets(ds.find(it[1]), it[i]);
                email_name[it[i]] = name;
            }
        }

        // Group emails by root
        unordered_map<string,vector<string>> comb;
        unordered_set<string> seen;
        for(auto it: accounts){
            for(int i = 1; i < it.size(); i++){
                if(seen.insert(it[i]).second){
                    comb[ds.find(it[i])].push_back(it[i]);
                }
            }
        }

        vector<vector<string>> res;
        for(auto& it: comb){
            string name = email_name[it.first];
            sort(it.second.begin(), it.second.end());
            vector<string> temp = it.second;
            temp.insert(temp.begin(), name);
            res.push_back(temp);
        }
        return res;
    }
};
```

### 🛠️ Optimizations

- **Avoid duplicate grouping:** Use a `seen` set instead of calling `unique()` which is `O(n)`.
    
- **Avoid unnecessary** `**********************find**********************` **calls:** Once you `find(root)` for an email, reuse it.
    

---

## 🔄 Alternate Approach: Graph + DFS

### ✅ Intuition:

- Treat each email as a node in a graph.
    
- Add undirected edges between emails in the same account.
    
- Use DFS to find all connected components.
    

### 💡 Why it works:

- Connected components in the graph = merged accounts.
    

### 🧱 Code:

```cpp
class Solution {
public:
    vector<vector<string>> accountsMerge(vector<vector<string>>& accounts) {
        unordered_map<string, vector<string>> graph;
        unordered_map<string, string> emailToName;

        for (auto& account : accounts) {
            string name = account[0];
            for (int i = 1; i < account.size(); ++i) {
                emailToName[account[i]] = name;
                if (i > 1) {
                    graph[account[1]].push_back(account[i]);
                    graph[account[i]].push_back(account[1]);
                } else {
                    graph[account[1]];
                }
            }
        }

        unordered_set<string> visited;
        vector<vector<string>> res;

        for (const auto& [email, _] : graph) {
            if (visited.count(email)) continue;

            vector<string> component;
            stack<string> stk;
            stk.push(email);
            visited.insert(email);

            while (!stk.empty()) {
                string curr = stk.top(); stk.pop();
                component.push_back(curr);
                for (string& neighbor : graph[curr]) {
                    if (!visited.count(neighbor)) {
                        stk.push(neighbor);
                        visited.insert(neighbor);
                    }
                }
            }

            sort(component.begin(), component.end());
            component.insert(component.begin(), emailToName[email]);
            res.push_back(component);
        }

        return res;
    }
};
```

---

## 🆚 Comparison

|Feature|Union-Find|DFS Graph Approach|
|---|---|---|
|Performance|Very efficient (`O(α(n))`)|Slightly slower in some cases|
|Code Complexity|Needs DSU class|Simpler with standard DFS|
|Intuition|Set merging abstraction|Graph traversal|

---

## 📌 Final Verdict

Both approaches are solid. If you're comfortable with Union-Find and want constant-time merge and find operations, go for it. If you prefer graph traversal or find Union-Find too abstract, DFS is a very readable and valid alternative.

# Accounts Merge - Union-Find vs DFS (Obsidian Notes)

## Problem Overview

Given a list of accounts, where each account is represented by a name and a list of emails, the task is to merge accounts belonging to the same person. Two accounts belong to the same person if they share at least one common email.

## 🧠 Intuition

- All emails in a single account are definitely connected.
    
- If any email in one account is also present in another account, then the accounts are indirectly connected.
    
- Our goal is to find connected components of emails.
    

---

## 🧩 Approach 1: Union-Find (Disjoint Set)

### ✅ Intuition:

- Each email is a node in the union-find data structure.
    
- Emails belonging to the same account are unioned together.
    
- After union operations, find all root emails and group all emails belonging to the same root.
    

### 🧱 Union-Find Structure:

```cpp
class DisjointSetString {
private:
    unordered_map<string, string> parent;
public:
    DisjointSetString() {}

    string find(const string& x){
        if(parent.find(x) == parent.end()){
            parent[x] = x;
        }
        if(parent[x] != x){
            parent[x] = find(parent[x]); // Path compression
        }
        return parent[x];
    }

    void unionSets(const string& x, const string& y){
        string xRoot = find(x);
        string yRoot = find(y);
        if(xRoot != yRoot){
            parent[yRoot] = xRoot;
        }
    }

    bool connected(const string& x, const string& y){
        return find(x) == find(y);
    }
};
```

### ❓ Doubt:

> Are we flattening the tree in the `find` function?

- Yes, the second `if` in `find` is path compression, which flattens the tree.
    

> Can this create skewed trees?

- Yes, which is why rank-based unioning is sometimes used. This solution skips it for simplicity.
    

---

## 🚀 Solution Code Using Union-Find

```cpp
class Solution {
public:
    vector<vector<string>> accountsMerge(vector<vector<string>>& accounts) {
        unordered_map<string,string> email_name;
        DisjointSetString ds;

        // Union emails in the same account
        for(auto it: accounts){
            string name = it[0];
            email_name[it[1]] = name;
            for(int i = 2; i < it.size(); i++){
                ds.unionSets(ds.find(it[1]), it[i]);
                email_name[it[i]] = name;
            }
        }

        // Group emails by root
        unordered_map<string,vector<string>> comb;
        unordered_set<string> seen;
        for(auto it: accounts){
            for(int i = 1; i < it.size(); i++){
                if(seen.insert(it[i]).second){
                    comb[ds.find(it[i])].push_back(it[i]);
                }
            }
        }

        vector<vector<string>> res;
        for(auto& it: comb){
            string name = email_name[it.first];
            sort(it.second.begin(), it.second.end());
            vector<string> temp = it.second;
            temp.insert(temp.begin(), name);
            res.push_back(temp);
        }
        return res;
    }
};
```

### 🛠️ Optimizations

- **Avoid duplicate grouping:** Use a `seen` set instead of calling `unique()` which is `O(n)`.
    
- **Avoid unnecessary** `**********************find**********************` **calls:** Once you `find(root)` for an email, reuse it.
    

---

## 🔄 Alternate Approach: Graph + DFS

### ✅ Intuition:

- Treat each email as a node in a graph.
    
- Add undirected edges between emails in the same account.
    
- Use DFS to find all connected components.
    

### 💡 Why it works:

- Connected components in the graph = merged accounts.
    

### 🧱 Code:

```cpp
class Solution {
public:
    vector<vector<string>> accountsMerge(vector<vector<string>>& accounts) {
        unordered_map<string, vector<string>> graph;
        unordered_map<string, string> emailToName;

        for (auto& account : accounts) {
            string name = account[0];
            for (int i = 1; i < account.size(); ++i) {
                emailToName[account[i]] = name;
                if (i > 1) {
                    graph[account[1]].push_back(account[i]);
                    graph[account[i]].push_back(account[1]);
                } else {
                    graph[account[1]];
                }
            }
        }

        unordered_set<string> visited;
        vector<vector<string>> res;

        for (const auto& [email, _] : graph) {
            if (visited.count(email)) continue;

            vector<string> component;
            stack<string> stk;
            stk.push(email);
            visited.insert(email);

            while (!stk.empty()) {
                string curr = stk.top(); stk.pop();
                component.push_back(curr);
                for (string& neighbor : graph[curr]) {
                    if (!visited.count(neighbor)) {
                        stk.push(neighbor);
                        visited.insert(neighbor);
                    }
                }
            }

            sort(component.begin(), component.end());
            component.insert(component.begin(), emailToName[email]);
            res.push_back(component);
        }

        return res;
    }
};
```

---

## 🆚 Comparison

|   |   |   |
|---|---|---|
|Feature|Union-Find|DFS Graph Approach|
|Performance|Very efficient (`O(α(n))`)|Slightly slower in some cases|
|Code Complexity|Needs DSU class|Simpler with standard DFS|
|Intuition|Set merging abstraction|Graph traversal|

---

## 📌 Final Verdict

Both approaches are solid. If you're comfortable with Union-Find and want constant-time merge and find operations, go for it. If you prefer graph traversal or find Union-Find too abstract, DFS is a very readable and valid alternative.