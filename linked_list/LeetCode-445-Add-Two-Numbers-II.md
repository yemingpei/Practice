### LeetCode-445-Add-Two-Numbers-II

> 题目链接

[LeetCode-445-Add-Two-Numbers-II](https://leetcode.com/problems/add-two-numbers-ii/)

> 思路

先反转链表，然后相加，开始拼接数字，进位单独保存。

> 代码

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        l1 = reverseList(l1);
        l2 = reverseList(l2);
        int current = 0;
        ListNode resHead = new ListNode(0), res = resHead;
        while (l1 != null || l2 != null) {
            if (l1 != null) {
                current += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                current += l2.val;
                l2 = l2.next;
            }
            ListNode node = new ListNode(current % 10);
            node.next = res.next;
            res.next = node;
            current = current / 10;
        }
        if (current > 0) {
            ListNode node = new ListNode(current);
            node.next = res.next;
            res.next = node;
        }
        return resHead.next;
    }
    
    public ListNode reverseList(ListNode head) {
        ListNode last = null;
        while(head != null) {
            ListNode tmp = head.next;
            head.next = last;
            last = head;
            head = tmp;    
        }    
        return last;
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(m + n)

额外使用int常量来辅助，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 98.70% of Java online submissions for Add Two Numbers II.

Memory Usage: 39.1 MB, less than 82.16% of Java online submissions for Add Two Numbers II.
