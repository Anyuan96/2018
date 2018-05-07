# 问题分析

给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：

	一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。
	示例 1:
	
	给定二叉树 [3,9,20,null,null,15,7]
	
	    3
	   / \
	  9  20
	    /  \
	   15   7
	返回 true 。
	
	示例 2:
	
	给定二叉树 [1,2,2,3,3,null,null,4,4]
	
	       1
	      / \
	     2   2
	    / \
	   3   3
	  / \
	 4   4
	返回 false 。
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
bool isBalanced(struct TreeNode* root) {
    int depth(struct TreeNode *root){
        if(root == NULL) return 0;
        int ldepth = depth(root->left);
        int rdepth = depth(root->right);
        return ldepth > rdepth ? ldepth+1 : rdepth+1;
    }
    if (root == NULL) return true;
    if (abs(depth(root->right) - depth(root->left)) > 1) return false;
    return isBalanced(root->left)&&isBalanced(root->right);
}
```
# 总结体会
本题还是运用了递归的思路，先判断左右两支的最大深度是否符合平衡条件，然后在分别判断左右两支的平衡性。