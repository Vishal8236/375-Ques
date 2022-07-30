## Subarray Product Less Than K

[Problem link](https://leetcode.com/problems/subarray-product-less-than-k/)

Given an array of integers nums and an integer k, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than k.

    
**Example 1:**

```
Input: nums = [10,5,2,6], k = 100
Output: 8
Explanation: The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6] Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
```

**Example 2:**

```
Input: nums = [1,2,3], k = 0
Output: 0
```

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        if(k<=1) return 0;
        
        int f=0, s=0, n = nums.size(), ans = 0, temp = 1;
        while(s<n)
        {
            temp *= nums[s];            
            while(temp >= k) temp /= nums[f++];
            ans += 1 + (s-f);
            s++;
        }
        return ans;
    }
};
``` 