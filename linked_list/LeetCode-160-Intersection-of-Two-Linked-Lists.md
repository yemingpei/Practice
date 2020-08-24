### LeetCode-160-Intersection-of-Two-Linked-Lists

> 题目链接

[LeetCode-160-Intersection-of-Two-Linked-Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

> 思路

双指针开始走，A指针从链表A走完时候，从链表B继续走，B指针从链表B走完时候，从链表A继续走，两者相等时，为重合的链表节点，若不相交，则会返回空

> 代码

```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode startA = headA;
        ListNode startB = headB;
        while(startA != startB){
            startA = startA == null? headB : startA.next;
            startB = startB == null? headA : startB.next;
        }
        return startA;
    }
}
```

> 复杂度分析

两个指针一个走完A就走B，一个走完B就走A，相同的时候就是相遇点，时间复杂度O(m + n)

额外使用了双指针指针，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.35% of Java online submissions for Intersection of Two Linked Lists.

Memory Usage: 42.6 MB, less than 55.01% of Java online submissions for Intersection of Two Linked Lists.
