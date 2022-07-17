## Validate Binary Search Tree

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

1. The left subtree of a node contains only nodes with keys less than the node's key.
2. The right subtree of a node contains only nodes with keys greater than the node's key.
3. Both the left and right subtrees must also be binary search trees.
 

**Example 1:**

![this is image](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)
```
Input: root = [2,1,3]
Output: true
```

**Example 2:**

![this is image](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

```
Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```

```cpp
class Solution {
public:
    void inOrder(TreeNode* root) {
        if (!root)
            return;
        inOrder(root->left);
        tree.push_back(root->val);
        inOrder(root->right);
    }
   
    bool isValidBST(TreeNode* root) {
        if (!root)
            return true;
        
        inOrder(root);
        for (int i=1; i<tree.size(); i++)
            if (tree[i] <= tree[i-1])
                return false;
        return true;
    }
private:
    vector<int> tree;
};
```