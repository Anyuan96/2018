# 问题分析

删除链表中等于给定值 val 的所有节点。

	示例:
	
	输入: 1->2->6->3->4->5->6, val = 6
	输出: 1->2->3->4->5
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* removeElements(struct ListNode* head, int val) {
    if (head == NULL) return NULL;
    if (head->next == NULL & head->val == val) return NULL;
    if (head->next == NULL & head->val != val) return head;
    while(head->val == val) {
        head = head->next;
        if (head == NULL) 
            return NULL;
    }
    struct ListNode *p;
    struct ListNode *pf;
    p = head;
    pf = p->next;
    while(pf){
        if ( pf->val == val){
            p->next = pf->next;
        } 
        else{
            p = p->next;

        }
        pf = p->next;
    }
    return head;
}
```
# 总结体会
如果链表是个空链表或者只有一个节点且与目标值相同则直接返回NULL。还要将链表前几个与目标值相同的节点删除再进行下面的步骤。我们定义两个链表p和pf，pf指向p的下一个节点，然后当pf节点的值与目标值相同时，就删除此节点，也就是p的下一节点指向pf的下一节点；否则，p就向下一个节点移动。