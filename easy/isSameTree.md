# 问题分析
	给定两个二叉树，编写一个函数来检验它们是否相同。
	
	如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。
	示例 1:
	
	输入:       1         1
	          / \       / \
	         2   3     2   3
	
	        [1,2,3],   [1,2,3]
	
	输出: true
	示例 2:
	
	输入:      1          1
	          /           \
	         2             2
	
	        [1,2],     [1,null,2]
	
	输出: false
	示例 3:
	
	输入:       1         1
	          / \       / \
	         2   1     1   2
	
	        [1,2,1],   [1,1,2]
	
	输出: false
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
bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if(p==NULL&&q==NULL)  
        return true;  
    else if(p==NULL)  
        return false;  
    else if(q==NULL)  
        return false;  
    else if(p->val!=q->val)  
        return false;  
    else  
        return (isSameTree(p->left,q->left))&&(isSameTree(p->right,q->right));  
}
```
# 总结体会
	该题目使用的是递归的方法，当某个结点的值相同时，则调用自身判断该节点左侧的树和右侧的数是否相同