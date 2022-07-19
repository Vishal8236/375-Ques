## Count BST nodes that lie in a given range

[Problem link](https://practice.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/1)

Given a Binary Search Tree (BST) and a range l-h(inclusive), count the number of nodes in the BST that lie in the given range.

1. The values smaller than root go to the left side
2. The values greater and equal to the root go to the right side

**Example 1:**
```
Input:
      10
     /  \
    5    50
   /    /  \
  1    40  100

l = 5, h = 45
Output: 3
Explanation: 5 10 40 are the node in the range
```

**Example 2:**
```
Input:
     5
    /  \
   4    6
  /      \
 3        7
l = 2, h = 8
Output: 5
Explanation: All the nodes are in the given range.
```


```cpp
    class Solution{
    public:
        int f(Node *root, int l, int h)
        {
            if(!root) return 0;
            
            int ans = 1;
            if(root->data > h or root->data < l) ans = 0;
            
            return ans + f(root->left, l, h)+f(root->right, l, h);
            
        }
        int getCount(Node *root, int l, int h)
        {
        // your code goes here  
        return f(root, l, h);
        }
    };
```

