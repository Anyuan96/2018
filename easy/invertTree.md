# 问题分析

翻转一棵二叉树。

	示例：
	
	输入：
	
	     4
	   /   \
	  2     7
	 / \   / \
	1   3 6   9
	输出：
	
	     4
	   /   \
	  7     2
	 / \   / \
	9   6 3   1
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
struct TreeNode* invertTree(struct TreeNode* root) {
    if (root == NULL) return NULL;
    struct TreeNode *temp;
    temp = root->left;
    root->left = invertTree(root->right);
    root->right = invertTree(temp);
    return root;
}
```
# 问题分析
这道题的解题思路还是递归，将左边翻转然后将右边翻转就可以了。