# 问题分析

请判断一个链表是否为回文链表。

	示例 1:
	
	输入: 1->2
	输出: false
	示例 2:
	
	输入: 1->2->2->1
	输出: true
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool isPalindrome(struct ListNode* head) {
    if (head == NULL || head->next == NULL) return true;
    int a[100000];
    int i = 0;
    while(head){
        a[i++] = head->val;
        head = head->next;
    }
    for (int j = 0; j <= i/2; j++){
        if (a[j] != a[i-j-1]) return false;
    }
    return true;
}
```
# 总结体会
现将链表里的所有值存储到一个数组中，然后判断这个数组是否是对称的就能解决了。