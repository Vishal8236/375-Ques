## Flatten Binary Tree to Linked List

[Problem link](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

Given the root of a binary tree, flatten the tree into a "linked list":

1. The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.
2. The "linked list" should be in the same order as a pre-order traversal of the binary tree.

Example 1:
![this is image](https://assets.leetcode.com/uploads/2021/01/14/flaten.jpg)
```
Input: root = [1,2,5,3,4,null,6]
Output: [1,null,2,null,3,null,4,null,5,null,6]
```

Example 2:
```
Input: root = []
Output: []
```

Example 3:
```
Input: root = [0]
Output: [0]
```

```cpp
class Solution {
public:
    TreeNode* dfs(TreeNode* root)
    {
        if(!root) return NULL;
        
        if(!root->right and !root->left) return root;
        
        TreeNode* cu = root;
        
        TreeNode* l = dfs(root->left);
        TreeNode* r = dfs(root->right);
        if(l != NULL)
        {
            if(r != NULL) l->right = cu->right;
            cu->right = cu->left;
            cu->left = NULL;
        }
        return r != NULL ? r : l;
    }
    void flatten(TreeNode* root) {
        dfs(root);
        return;
    }
};
```