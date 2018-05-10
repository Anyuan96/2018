# 问题分析

给定一个链表，判断链表中是否有环。
#代码实现
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {
    if (head == NULL) return false;
    struct ListNode *p;
    struct ListNode *q;
    p = head;
    q = head;
    while(p&&q&&q->next){
        p = p->next;
        q = q->next->next;
        if (p == q) return true;
    }
    return false;
}
```
# 总结体会
本题用了两个指针，一个快指针一个慢指针，来对链表进行遍历，如果遇到NULL了，则说明不可能是环形链表。若快慢指针能指向相同的地址，则是环形链表。