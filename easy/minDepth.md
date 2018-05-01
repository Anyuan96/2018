# 问题分析
	给定一个二叉树，找出其最小深度。
	
	最小深度是从根节点到最近叶子节点的最短路径上的节点数量。
	
	说明: 叶子节点是指没有子节点的节点。
	
	示例:
	
	给定二叉树 [3,9,20,null,null,15,7],
	
	    3
	   / \
	  9  20
	    /  \
	   15   7
	返回它的最小深度  2.
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
int minDepth(struct TreeNode* root) {
    if (root == NULL) return 0;
    if (root->left == NULL) return minDepth(root->right)+1;
    if (root->right == NULL) return minDepth(root->left)+1;
    int minLeft = minDepth(root->left);
    int minRight = minDepth(root->right);
    return minLeft < minRight ? minLeft+1:minRight+1;
}
```
# 总结体会
这道题跟maxDepth差不多，但是当root第一个结点的只有单个分支时，则返回另一边的最小深度值，然后用递归的方法进行计算最小深度值。