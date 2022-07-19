## Kth Smallest Element in a BST

[Problem Link](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.


**Example 1:**

![this is image](https://assets.leetcode.com/uploads/2021/01/28/kthtree1.jpg)

```
Input: root = [3,1,4,null,2], k = 1
Output: 1
```

**Example 2:**

![this is image](https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg)

```
Input: root = [5,3,6,2,4,null,null,1], k = 3
Output: 3
```


```cpp
    class Solution {
    public:
        int res;
        void f(TreeNode* root, int k, int& c)
        {
            if(!root) return;
            f(root->left, k, c);
            c++;
            if(c == k) res = root->val;
            f(root->right, k, c);
            return;
        }
        int kthSmallest(TreeNode* root, int k) {
            int c = 0;
            f(root, k, c);
            return res;
        }
    };
```

**Hint**

Try in-order traversal to solve this problem.