## Activity selection problem greedy algo

Given N activities with their start and finish day given in array start[] and end[]. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a given day.

The greedy choice is to always pick the next activity whose finish time is least among the remaining activities and the start time is more than or equal to the finish time of the previously selected activity. We can sort the activities according to their finishing time so that we always consider the next activity as minimum finishing time activity.
1) Sort the activities according to their finishing time 

2) Select the first activity from the sorted array and print it. 

3) Do the following for the remaining activities in the sorted array. 

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


