# 问题分析
计算给定二叉树的所有左叶子之和。

	示例：
	
	    3
	   / \
	  9  20
	    /  \
	   15   7
	
	在这个二叉树中，有两个左叶子，分别是 9 和 15，所以返回 24
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
int sumOfLeftLeaves(struct TreeNode* root) {
    if (root == NULL) return 0;
    if (root->left != NULL && root->left->left == NULL && root->left->right == NULL)
        return root->left->val + sumOfLeftLeaves(root->right);
    else
        return sumOfLeftLeaves(root->left) + sumOfLeftLeaves(root->right);
}
```
# 总结体会
这道题的思想是先找到左叶子，然后用递归的方法进行计算。