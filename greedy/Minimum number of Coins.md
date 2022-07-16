## Minimum number of Coins

Given an infinite supply of each denomination of Indian currency { 1, 2, 5, 10, 20, 50, 100, 200, 500, 2000 } and a target value N.
Find the minimum number of coins and/or notes needed to make the change for Rs N.

```cpp
class Solution{
public:
    vector<int> minPartition(int N)
    {
        // code here
        vector<int> temp = {1,2,5,10,20,50,100,200,500,2000};
        int len = temp.size();
        
        vector<int> res;
        int i=len-1;
        while(N>0)
        {
            if(N<temp[i])
            {
                i--;
            }
            else{
                res.push_back(temp[i]);
                N -= temp[i];
            }
        }
        return res;
    }
};
```

**Example 1:**

Input: N = 43
Output: 20 20 2 1
Explaination: Minimum number of coins and notes needed  to make 43. 


**Example 2:**

Input: N = 1000
Output: 500 500
Explaination: minimum possible notes is 2 notes of 500.

**Algorithm:**

1. Sort the array of coins in decreasing order.
2. Initialize result as empty.
3. Find the largest denomination that is smaller than current amount.
4. Add found denomination to result. Subtract value of found denomination from amount.
5. If amount becomes 0, then print result.
6. Else repeat steps 3 and 4 for new value of V.