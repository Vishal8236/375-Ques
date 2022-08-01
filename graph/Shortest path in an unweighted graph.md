## Shortest path in an unweighted graph

[Problem link](https://www.codingninjas.com/codestudio/problems/shortest-path-in-an-unweighted-graph_981297?leftPanelTab=0&utm_source=youtube&utm_medium=affiliate&utm_campaign=Lovebabbar)

The city of Ninjaland is analogous to the unweighted graph. The city has ‘N’ houses numbered from 1 to ‘N’ respectively and are connected by M bidirectional roads. If a road is connecting two houses ‘X’ and ‘Y’ which means you can go from ‘X’ to ‘Y’ or ‘Y’ to ‘X’. It is guaranteed that you can reach any house from any other house via some combination of roads. Two houses are directly connected by at max one road.

A path between house ‘S’ to house ‘T’ is defined as a sequence of vertices from ‘S’ to ‘T’. Where starting house is ‘S’ and the ending house is ‘T’ and there is a road connecting two consecutive houses. Basically, the path looks like this: (S , h1 , h2 , h3 , ... T). you have to find the shortest path from ‘S’ to ‘T’.

In the below map of Ninjaland let say you want to go from S=1 to T=8, the shortest path is (1, 3, 8). You can also go from S=1 to T=8  via (1, 2, 5, 8)  or (1, 4, 6, 7, 8) but these paths are not shortest.

![img](https://files.codingninjas.in/pic1-6747.png)

Sample Input 1 :
```
1
4 4
1 4
1 2
2 3
3 4
1 3
```

Sample Output 1 :
```
( 1 , 3 , 4 )
```

```cpp
#include<bits/stdc++.h>
vector<int> shortestPath( vector<pair<int,int>> edges , int n , int m, int s , int t){
    // Write your code here
    unordered_map<int, vector<int>> adj;
    for(int i=0; i<m; i++)
    {
        int u = edges[i].first;
        int v = edges[i].second;
        
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
    
    unordered_map<int, bool> visi;
    unordered_map<int,int> parent;
    queue<int> q;
    q.push(s);
    visi[s] = true;
    parent[s] = -1;
    
    while(!q.empty())
    {
        int node = q.front();
        q.pop();
        
        for(auto it : adj[node])
        {
            if(visi[it] == false)
            {
                visi[it] = true;
                parent[it] = node;
                q.push(it);
            }
        }
    }
    //parent shortest path
    vector<int> ans;
    int cu = t;
    ans.push_back(t);
    while(cu != s)
    {
        cu = parent[cu];
        ans.push_back(cu);
    }
    reverse(ans.begin(), ans.end());
    return ans;
}
```