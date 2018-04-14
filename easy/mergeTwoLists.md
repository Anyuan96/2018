# 问题分析
	将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 
	
	示例：
	
	输入：1->2->4, 1->3->4
	输出：1->1->2->3->4->4
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {     
    typedef struct ListNode  listnode;
    listnode *head;
    listnode *nextlist;
    if(l1 == NULL ) return l2;  
    if(l2 == NULL ) return l1;  
    if(l1->val > l2->val){  
       nextlist = l2;  
       l2=l2->next;   
    }else{  
       nextlist = l1;  
       l1=l1->next;  
    }  
    head= nextlist;  
    while(l1&&l2){  
        if(l1->val > l2->val){  
          nextlist->next = l2;  
          l2 = l2->next;  
        }
        else{  
          nextlist->next = l1;  
          l1 = l1->next;  
        }  
        nextlist = nextlist ->next;  
    }  
    if(l1)  
        nextlist->next = l1;  
    else  
        nextlist->next = l2;  
    return head;
}  
```
# 总结体会
	1. 链表的操作用->
	2. 要给链表指定next地址
