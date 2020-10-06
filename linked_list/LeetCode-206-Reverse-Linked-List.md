### LeetCode-206-Reverse-Linked-List

> 题目链接

[LeetCode-206-Reverse-Linked-List](https://leetcode.com/problems/reverse-linked-list/)

> 思路

反转列表，需要先行节点来记录头，临时节点来记录下一个位置

> 代码

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode root = new ListNode();
        while(head != null){
            ListNode node = head.next;
            head.next = root.next;
            root.next = head;
            head = node;
        }
        return root.next;
    }
}
```

> 复杂度分析

遍历整个链表，时间复杂度O(n)

额外使用node来记录下一个位置，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Reverse Linked List.

Memory Usage: 38.7 MB, less than 94.63% of Java online submissions for Reverse Linked List.
