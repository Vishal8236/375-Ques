## Delete Node in a BST

[Problem link](https://leetcode.com/problems/delete-node-in-a-bst/)

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:

1. Search for a node to remove.
2. If the node is found, delete the node.
 

**Example 1:**
```
![This is image](https://assets.leetcode.com/uploads/2020/09/04/del_node_1.jpg)

Input: root = [5,3,6,2,4,null,7], key = 3

Output: [5,4,6,2,null,null,7]

Explanation: Given key to delete is 3. So we find the node with value 3 and delete it.

One valid answer is [5,4,6,2,null,null,7], shown in the above BST.

![This is image](https://assets.leetcode.com/uploads/2020/09/04/del_node_supp.jpg)

Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
```

**Example 2:**
```
Input: root = [5,3,6,2,4,null,7], key = 0
Output: [5,3,6,2,4,null,7]
Explanation: The tree does not contain a node with value = 0.
```

```cpp
class Solution {
public:
    TreeNode* deleteNode(TreeNode* root, int key) {
        if(!root){
            return NULL;  
        } 
        
        //If root value is target key
        if(root->val == key)
        {
            return helper(root);
        }
            
        //if root is not a target key
        TreeNode* dummy = root;
        while(root != NULL)
        {
            if(root->val > key)
            {
                if(root->left != NULL and root->left->val == key)
                {
                    root->left = helper(root->left);
                    break;
                }else{
                    root = root->left;
                }
            }
            else{
                if(root->right != NULL and root->right->val == key)
                {
                    root->right = helper(root->right);
                    break;
                }else{
                    root = root->right;
                }
            }
        }
        return dummy;
    }
    
    
    TreeNode* helper(TreeNode* root){
        if(root->left == NULL) return root->right;
        else if(root->right == NULL) return root->left;
        
        TreeNode* rightnode = root->right;
        TreeNode* lastnode = findLast(root->left);
        lastnode->right = rightnode;
        return root->left;
    }
    
    TreeNode* findLast(TreeNode* root)
    {
        if(root->right == NULL) return root;
        
        return findLast(root->right);
    }
};
```