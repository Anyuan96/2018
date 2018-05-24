# 问题分析

反转一个单链表。

	示例:
	
	输入: 1->2->3->4->5->NULL
	输出: 5->4->3->2->1->NULL
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    if(head == NULL || head->next == NULL) return head;
    struct ListNode *first=NULL;  
    struct ListNode *second=head;  
    struct ListNode *third=NULL;  
    while(second)  
    {  
        third=second->next;  
        second->next=first;  
        first=second;  
        second=third;  
    }  
    return first;  
} 
```
# 代码实现
首先我们要先定义三个链表指针，将second指向给定的head，将second的下一节点存储到third里，first指向当前处理节点的前一个节点，然后翻转节点指针的指向，将当前seconde的下一节点存储到third里面，然后将second的下一节点指向first，也就是翻转节点，最后second和first都想前移一个节点（原链表的给定顺序）。