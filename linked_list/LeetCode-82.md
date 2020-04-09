### LeetCode-82-Remove-Duplicates-from-Sorted-List-II

> 题目链接

[LeetCode-82-Remove-Duplicates-from-Sorted-List-II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

> 思路

一个指针负责输出，一个指针负责遍历，遇到相同的值就更新number，不相同，则加入到输出指针的next位置

> 代码

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null)return head;
        ListNode resultList = new ListNode(0);
        ListNode start = resultList;
        ListNode p = head;
        int number = head.val - 1;
        while (p != null) {
          if (p.val != number)
            if (p.next == null || p.val != p.next.val) {
              start.next = p;
              start = start.next;
            } else {
              number = p.val;
            }
          p = p.next;
        }
        start.next = null;
        return resultList.next;
    }
}
```

> 复杂度分析

遍历了一遍链表，时间复杂度O(n)

额外使用了三个指针，一个常量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Remove Duplicates from Sorted List II.
Memory Usage: 39.3 MB, less than 6.98% of Java online submissions for Remove Duplicates from Sorted List II.
