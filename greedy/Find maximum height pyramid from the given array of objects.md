## Find maximum height pyramid from the given array of objects

[Problem link](https://www.geeksforgeeks.org/find-maximum-height-pyramid-from-the-given-array-of-objects/)

Given n objects, with each object has width wi. We need to arrange them in a pyramidal way such that : 
 
1. Total width of ith is less than (i + 1)th.
2. Total number of objects in the ith is less than (i + 1)th.

![This is image](https://media.geeksforgeeks.org/wp-content/uploads/maximumHeightPyramid-1.jpg)

maximum height pyramid from the given array of objects
The task is to find the maximum height that can be achieved from given objects.

Examples : 
 
```
Input : arr[] = {40, 100, 20, 30}
Output : 2
Top level : 30 Lower (or bottom) level : 20, 40 and 100 Other possibility can be placing 20 on the top, and at second level any other 4 objects. Another possibility is to place 40 at top and other three at the bottom.

Input : arr[] = {10, 20, 30, 50, 60, 70}
Output : 3
```

```cpp
#include <bits/stdc++.h>
#include <iostream>
#include <vector>
using namespace std;

int findMaxHeight(vector<int> v)
{
    int ans = 1;
    
    int prev_width = v[0];
    int prev_count = 1;
    
    int curent_width = 0;
    int curent_count = 0;
    
    for(int i=1; i<v.size(); i++)
    {
        curent_width += v[i];
        curent_count += 1;
        
        if(curent_count > prev_count && curent_width > prev_width)
        {
            ans++;
    
            prev_width = curent_width;
            prev_count = curent_count;
    
            curent_count = 0;
            curent_width = 0;
        }
    }
    return ans;
}
int main() {
    vector<int> v = {40, 100, 20, 30, 200, 200};
    
    //first sort the array
    sort(v.begin(), v.end());
    
    int ans = findMaxHeight(v);    
    
    cout<<ans;
    
	return 0;
}
```