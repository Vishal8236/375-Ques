## Find a common element in all rows of a given row-wise sorted matrix

[Problem link](https://www.geeksforgeeks.org/find-common-element-rows-row-wise-sorted-matrix/)

Given a matrix where every row is sorted in increasing order. Write a function that finds and returns a common element in all rows. If there is no common element, then returns -1. 
Example: 
 
```
Input: mat[4][5] = { {1, 2, 3, 4, 5},
                    {2, 4, 5, 8, 10},
                    {3, 5, 7, 9, 11},
                    {1, 3, 5, 7, 9},
                  };
Output: 5
```

```cpp
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

int main() {
    int m = 4, n = 5;
    vector<vector<int>> mat = {
        { 1, 2, 3, 4, 6 },
        { 2, 4, 5, 8, 10 },
        { 3, 5, 7, 9, 11 },
        { 1, 3, 5, 7, 9 },
    };
    
    unordered_map<int, int> mp;
    for(int i=0; i<n; i++)
    {
        mp[mat[0][i]]++;
    }
    
    for(int i=1; i<m; i++)
    {
        for(int j=0; j<n; j++)
        {
            mp[mat[i][j]]++;
        }
    }
    
    for(auto it : mp)
    {
        if(it.second == m)
        {
            cout<<it.first<<" is repeated element."<<endl;
        }
    }
    cout<<"No element is found";
	return 0;
}
```