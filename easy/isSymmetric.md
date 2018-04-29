# 问题分析
	给定一个二叉树，检查它是否是镜像对称的。
	
	例如，二叉树 [1,2,2,3,4,4,3] 是对称的。
	
	    1
	   / \
	  2   2
	 / \ / \
	3  4 4  3
	但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:
	
	    1
	   / \
	  2   2
	   \   \
	   3    3
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
bool isSymmetric(struct TreeNode* root) {
     bool isTrue(struct TreeNode* left, struct TreeNode* right){  
     if (left == NULL && right == NULL) return true;  
     if (left == NULL) return false;  
     if (right == NULL) return false;  
     return ((left->val == right->val)
             &&isTrue(left->left,right->right)
             &&isTrue(left->right,right->left));
    }  
    if (root == NULL) return true;
    return isTrue(root->left, root->right);
} 
```
# 总结体会
	这个题目和上个题目的有相似之处，但是本题是判断一个二叉树是否是对称的。
	需要额外定义一个函数来判断二叉树的分支是否相同，也就是说二叉树的左边的
	左边和右边的右边是否相同，左边的右边和右边的左边是否相同。然后用递归的
	方法来判断每个节点以及节点下面的树是否是对称的