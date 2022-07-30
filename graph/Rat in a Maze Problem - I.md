## Rat in a Maze Problem - I

[Problem link](https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

Consider a rat placed at (0, 0) in a square matrix of order N * N. It has to reach the destination at (N - 1, N - 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are 'U'(up), 'D'(down), 'L' (left), 'R' (right). Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.
Note: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell.

```
Example 1:

Input:
N = 4
m[][] = {{1, 0, 0, 0},
         {1, 1, 0, 1}, 
         {1, 1, 0, 0},
         {0, 1, 1, 1}}

Output: DDRDRR DRDDRR
Explanation: The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR  and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.

Example 2:

Input:
N = 2
m[][] = {{1, 0},
         {1, 0}}
Output: -1
Explanation: No path exists and destination cell is blocked.
```

```cpp
class Solution{
    public:
    vector<string> ans;
    void solve(vector<vector<int>> &m,int i,int j,int n,vector<vector<bool>> &vis,string s){
        if(i<0 || j<0 || i>=n ||j >=n || vis[i][j] || m[i][j]==0)return;
        
        if(i==n-1 && j==n-1){
            ans.push_back(s);
            s="";
            return;
        }
        
        vis[i][j]=true;
        solve(m,i+1,j,n,vis,s+'D');
        solve(m,i,j-1,n,vis,s+'L');
        solve(m,i,j+1,n,vis,s+'R');
        solve(m,i-1,j,n,vis,s+'U');
        vis[i][j]=false;
    }
    
    vector<string> findPath(vector<vector<int>> &m, int n) {
        vector<vector<bool>> vis(n,vector<bool>(n,false));
        solve(m,0,0,n,vis,"");
        if(ans.size()!=0)return ans;
        return {"-1"};
    }
};
```