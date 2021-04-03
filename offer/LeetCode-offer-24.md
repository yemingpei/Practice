### LeetCode-offer-24

> 题目链接

[LeetCode-offer-24](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

> 思路

需要一个前置指针来标志开始的位置，然后改变前后的位置，一直到遍历结束

> 代码

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = new ListNode(0);
        while(head != null){
            ListNode node = head.next;
            head.next = pre.next;
            pre.next = head;
            head = node;
        }
        return pre.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用1个指针，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了59.11%的用户
