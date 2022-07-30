## Detect cycle in an undirected graph

[Problem link](https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

Given an undirected graph with V vertices and E edges, check whether it contains any cycle or not. 

**Example 1:**

```
Input:  
V = 5, E = 5
adj = {{1}, {0, 2, 4}, {1, 3}, {2, 4}, {1, 3}} 
Output: 1
Explanation:  1->2->3->4->1 is a cycle.
```

**Example 2:**

```
Input: 
V = 4, E = 2
adj = {{}, {2}, {1, 3}, {2}}
Output: 0
Explanation: No cycle in the graph.
```


```cpp
class Solution {
  public:
    // Function to detect cycle in an undirected graph.
    bool checkcycle(int i, vector<int> adj[], int v, vector<bool> &visi)
    {
        visi[i] = true;
        queue<int> q;
        q.push(i);
        unordered_map<int, int> mp;
        mp[i] = -1;
        
        while(!q.empty())
        {
            int node = q.front();
            for(auto it : adj[node])
            {
                if(mp[node] != it and visi[it])
                {
                    return true;
                }
                else if(visi[it] == false)
                {
                    q.push(it);
                    visi[it] = true;
                    mp[it] = node;
                }
            }
            q.pop();
        }
        return false;
    }
    bool isCycle(int V, vector<int> adj[]) {
        // Code here
        vector<bool> visi(V, false);
        for(int i=0; i<V; i++)
        {
            if(visi[i] == false)
            {
                if(checkcycle(i,adj,V, visi))
                {
                    return true;
                }
            }
        }
        return false;
    }
};
```

**Hint**

1. create one vector for check node is visited or not
2. traverse the node by BSF traversal and push all node in queue
3. also maintain the unordered_map to contain and check parent node 