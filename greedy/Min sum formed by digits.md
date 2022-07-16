## Min sum formed by digits

Given an array of digits (values are from 0 to 9), find the minimum possible sum of two numbers formed from digits of the array. All digits of given array must be used to form the two numbers.

```cpp
class Solution{
    public:
    long long int minSum(int arr[], int n)
    {
        // Your code goes here
        sort(arr, arr+n);
        
        if(n == 1) return arr[0];
        
        long long num1 = arr[0];
        long long num2 = arr[1];
        
        int j=2, k=3;
        for(int i=0; i<n/2-1; i++)
        {
            num1 *= 10;
            num2 *= 10;
            num1 += arr[j];
            num2 += arr[k];
            j += 2;
            k += 2;
        }
        if(k == n)
        {
            num1 *= 10;
            num1 += arr[n-1];
        }
        return num1+num2;
    }
};
```

**Example 1:**

```
Input:
N = 6
arr[] = {6, 8, 4, 5, 2, 3}
Output:604
Explanation: The minimum sum is formed by numbers 358 and 246
```

**Example 2:**

```
Input:
N = 5
arr[] = {5, 3, 0, 7, 4}
Output: 82
Explanation: The minimum sum is formed by numbers  35 and 047
```