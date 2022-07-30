## Detect cycle in a directed graph

[Problem link](https://practice.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)

Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, check whether it contains any cycle or not.

Example 1:

Input:

Output: 1
Explanation: 3 -> 3 is a cycle


```cpp
class Solution {
  public:
    // Function to detect cycle in a directed graph.
    bool checkForCycle(int node, int v, vector<int> adj[], vector<int> &visi, vector<int> &order)
    {
        visi[node] = true;
        order[node] = true; 
        for(auto it : adj[node])
        {
            if(!visi[it])
            {
                if(checkForCycle(it, v, adj, visi, order))
                {
                    return true;
                }
            }
            else if(order[it])
            {
                return true;
            }
            
        }
        order[node] = false;
        return false;
    }
    bool isCyclic(int V, vector<int> adj[])
    {
        vector<int> vis(V, 0);
        vector<int> order(V, 0);
        for (int i = 0; i < V; i++)
        {
            if (!vis[i])
            {
                if (checkForCycle(i, V, adj, vis, order))
                    return true;
            }
        }
        return false;
    }
};

//{ Driver Code Starts.

int main() {

    int t;
    cin >> t;
    while (t--) {
        int V, E;
        cin >> V >> E;

        vector<int> adj[V];

        for (int i = 0; i < E; i++) {
            int u, v;
            cin >> u >> v;
            adj[u].push_back(v);
        }

        Solution obj;
        cout << obj.isCyclic(V, adj) << "\n";
    }

    return 0;
}

```