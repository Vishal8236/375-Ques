## Topological Sort

[Problem link](https://www.codingninjas.com/codestudio/problems/topological-sort_982938?topList=love-babbar-dsa-sheet-problems&leftPanelTab=0&utm_source=youtube&utm_medium=affiliate&utm_campaign=Lovebabbar)

A Directed Acyclic Graph (DAG) is a directed graph that contains no cycles.

Topological Sorting of  DAG is a linear ordering of vertices such that for every directed edge from vertex ‘u’ to vertex ‘v’, vertex ‘u’ comes before ‘v’ in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG.

Given a DAG consisting of ‘V’ vertices and ‘E’ edges, you need to find out any topological sorting of this DAG.  Return an array of size ‘V’  representing the topological sort of the vertices of the given DAG.

![img](https://files.codingninjas.in/eg-6753.png)

In this graph, there are directed edges from 0 to 1 and 0 to 3, so 0 should come before 1 and 3. Also, there are directed edges from 1 to 2 and 3 to 2 so 1 and 3 should come before 2.

So, The topological sorting of this DAG is  {0 1 3 2}.

Note that there are multiple topological sortings possible for a DAG. For the graph given above one another topological sorting is: {0, 3, 1, 2}


```cpp
#include<bits/stdc++.h>
void f(int i, int v, unordered_map<int, vector<int>> &adj, vector<bool> &visi, stack<int> &temp)
{
    visi[i] = true;
    for(auto it : adj[i])
    {
        if(!visi[it])
        {
            f(it, v, adj, visi, temp);
        }
    }
    temp.push(i);    
}
vector<int> topologicalSort(vector<vector<int>> &edges, int v, int e)  {
    // Write your code here
    unordered_map<int, vector<int>> adj;
    
    for(int i=0; i<e; i++)
    {
        int u = edges[i][0];
        int v = edges[i][1];
        
        adj[u].push_back(v);
    }
    vector<int> res;
    stack<int> temp;
    vector<bool> visi(v, false);
    for(int i=0; i<v; i++)
    {
        if(visi[i] == false)
        {
            f(i, v, adj, visi, temp);
        }
    }
    while(!temp.empty())
    {
        res.push_back(temp.top());
        temp.pop();
    }
    return res;
}
```