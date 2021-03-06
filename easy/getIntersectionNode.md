# 问题分析
编写一个程序，找到两个单链表相交的起始节点。

 

例如，下面的两个链表：

	A:          a1 → a2
	                   ↘
	                     c1 → c2 → c3
	                   ↗            
	B:     b1 → b2 → b3
在节点 c1 开始相交。

 

注意：

如果两个链表没有交点，返回 null.
在返回结果后，两个链表仍须保持原有的结构。
可假定整个链表结构中没有循环。
程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。
# 代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    if (headA == NULL || headB == NULL) return NULL;
    struct ListNode *headOfB;
    headOfB = headB;
    while(headA){
        while(headB){
            if (headB == headA) return headA;
            headB = headB->next;
        }
        headA = headA->next;
        headB = headOfB;
    }
    return NULL;
}
```
# 总结体会
代码的主体是两个循环，来寻找两个单链表的交点。若存在指向地址相同的情况，则是相交链表，否则返回NULL。
