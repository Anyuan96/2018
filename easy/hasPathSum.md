# 问题分析
给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

说明: 叶子节点是指没有子节点的节点。

示例: 
给定如下二叉树，以及目标和 sum = 22，

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
返回 true, 因为存在目标和为 22 的根节点到叶子节点的路径 5->4->11->2。
# 代码实现
```C
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
bool hasPathSum(struct TreeNode *root, int sum) {
    if (root == NULL)
        return false;
    else if (!(root->left) && !(root->right)){
        if (root->val == sum)   
            return true;
        else   
            return false;
    }else {
        return hasPathSum(root->left, sum-root->val) || hasPathSum(root->right, sum - root->val);
    }
}
```
# 总结体会
本题的思想还是递归，在解决二叉树问题时，很多时候都用到了递归。每到一个节点的时候用sum减掉当前节点的值，最后判断到达叶子节点的时候的值是否与剩下的值相同。