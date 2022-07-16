## Activity selection problem greedy algo

Given N activities with their start and finish day given in array start[] and end[]. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a given day.


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

Input:
N = 2
start[] = {2, 1}
end[] = {2, 2}
Output: 1
Explanation: A person can perform only one of the given activities.

**Example 2:**

Input:
N = 4
start[] = {1, 3, 2, 5}
end[] = {2, 4, 3, 6}
Output: 3
Explanation: A person can perform activities 1, 2 and 4.


