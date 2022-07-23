## Permutations

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

```
Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
Example 2:

Input: nums = [0,1]
Output: [[0,1],[1,0]]
Example 3:

Input: nums = [1]
Output: [[1]]
```

```cpp
class Solution {
public:
    void f(int freq[], vector<int>& nums, vector<int> &ds ,vector<vector<int>> &ans)
    {
        if(ds.size() == nums.size())
        {
            ans.push_back(ds);
            return;
        }
            
        for(int i=0; i<nums.size(); i++)
        {
            if(!freq[i])
            {
                freq[i] = 1;
                ds.push_back(nums[i]);
                f(freq, nums, ds, ans);
                freq[i] = 0;
                ds.pop_back();
            }
        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> vec;
        
        vector<int> ds;
        
        int freq[nums.size()];
        
        for(int i=0; i<nums.size(); i++) freq[i] = 0;
                
        f(freq, nums, ds, vec);
            
        return vec;
    }
};
```

**Hint**

1. create one vector for store each permutation
2. this array for track that the element traverse or not
