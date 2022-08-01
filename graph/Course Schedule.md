## Course Schedule

[Problem link]()

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1. Return true if you can finish all courses. Otherwise, return false.


**Example 1:**

```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. To take course 1 you should have finished course 0. So it is possible.
```

**Example 2:**

```
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

```cpp
class Solution {
public:
    bool canFinish(int c, vector<vector<int>>& pre) {
        unordered_map<int, vector<int>> adj;
        
        int n = pre.size();
        for(int i=0; i<n; i++)
        {
            int u = pre[i][0];
            int v = pre[i][1];
            
            adj[u].push_back(v);
        }
        
        //find indgree
        vector<int> indgree(c, 0);
        for(auto it : adj)
        {
            for(auto j : it.second)
            {
                indgree[j]++;
            }
        }
        
        //push 0 in queue
        queue<int> q;
        for(int i=0; i<c; i++)
        {
            if(indgree[i] == 0)
            {
                q.push(i);
            }
        }
        
        //do bsf
        int count = 0;
        while(!q.empty())
        {
            int node = q.front();
            q.pop();
            
            count++;
            for(auto it : adj[node])
            {
                indgree[it]--;
                if(indgree[it] == 0){
                    q.push(it);  
                } 
            }
        }
        return count == c ? true : false;
    }
};
```


**Hint**

1. check if graph has cycle then return false if not then return true
2. use topological sort to check if cycle present or not
