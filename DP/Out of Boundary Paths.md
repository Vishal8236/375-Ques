## Out of Boundary Paths

There is an m x n grid with a ball. The ball is initially at the position [startRow, startColumn]. You are allowed to move the ball to one of the four adjacent cells in the grid (possibly out of the grid crossing the grid boundary). You can apply at most maxMove moves to the ball.

Given the five integers m, n, maxMove, startRow, startColumn, return the number of paths to move the ball out of the grid boundary. Since the answer can be very large, return it modulo 109 + 7.

**Example 1:**
![this is exmaple 1](https://assets.leetcode.com/uploads/2021/04/28/out_of_boundary_paths_1.png)
```
Input: m = 2, n = 2, maxMove = 2, startRow = 0, startColumn = 0
Output: 6
```

**Example 2:**
![this is exmpale 2](https://assets.leetcode.com/uploads/2021/04/28/out_of_boundary_paths_2.png)
```
Input: m = 1, n = 3, maxMove = 3, startRow = 0, startColumn = 1
Output: 12
```

```cpp
class Solution {
public:
    long mod = 1000000007;
    int f(int m, int n, int maxm, int i, int j, vector<vector<vector<int>>> &dp)
    {
        if(i<0 or j<0 or i==m or j==n) return 1;
        
        if(maxm == 0) return 0;
        
        if(dp[i][j][maxm] != -1) return dp[i][j][maxm];
        return dp[i][j][maxm] = (f(m, n, maxm-1, i+1, j, dp)%mod + f(m, n, maxm-1, i-1, j, dp)%mod + f(m, n, maxm-1, i, j+1, dp)%mod + f(m, n, maxm-1, i, j-1, dp)%mod)%mod;
    }
    int findPaths(int m, int n, int maxMove, int startRow, int startColumn) {
        vector<vector<vector<int>>> dp(m+2, vector<vector<int>>(n+2,  vector<int>(maxMove+1, -1)));
        return f(m,n,maxMove, startRow, startColumn, dp);
    }
};
```

**Algorithm**
1. create 3D matrix by max row, max column and max move;
2. Implement DFS and move left, right, bottom, top.
3. If i less then 0 or j less then 0 or i equal to max row or j is equal to max column then **return 1** because ball go outside of grid.
4. If max move is equal to the 0 then return 0 because we can not move further.
