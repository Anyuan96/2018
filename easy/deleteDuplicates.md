# 问题分析
	
	给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。
	
	示例 1:
	
	输入: 1->1->2
	输出: 1->2
	示例 2:
	
	输入: 1->1->2->3->3
	输出: 1->2->3
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* deleteDuplicates(struct ListNode* head) {
    if (head == NULL) return head;
    struct ListNode *headOflist;
    headOflist = head;
    while( head->next != NULL ){
        if ( head->val == head->next->val){
            head->next = head->next->next;
        } else{
            head = head->next;
        }
    }
    return headOflist;
}
```
# 总结体会
	遍历链表，比较当前的值与下一个值的大小，如果相等，下一跳的地址变为head->next->next。
