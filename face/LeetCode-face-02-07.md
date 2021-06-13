### LeetCode-face-02-07

> 题目链接

[LeetCode-face-02-07](https://leetcode-cn.com/problems/intersection-of-two-linked-lists-lcci/)

> 思路

遍历链表，到达尾部，则又从另一个链表的头部开始，直到找到两个一样的节点，如果没有重合就是null

> 代码

```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode node1 = headA;
        ListNode node2 = headB;
        while(node1 != node2){
            node1 = node1 == null ? headB : node1.next;
            node2 = node2 == null ? headA : node2.next;
        }
        return node1;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n + m)

额外使用两个指针，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.90%的用户

内存消耗：41.1 MB, 在所有 Java 提交中击败了62.62%的用户
