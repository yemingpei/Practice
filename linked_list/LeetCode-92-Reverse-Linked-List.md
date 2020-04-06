### LeetCode-92-Reverse-Linked-List-II

> 题目链接

[LeetCode-92-Reverse-Linked-List-II](https://leetcode.com/problems/reverse-linked-list-ii/)

> 思路

前后指针，添加辅助指针ListNode(0)，原地反转，注意特殊case，如m = 1的情况，不可以反回head，应该返回反转后的指针

> 代码

```java
class Solution {
    public ListNode reverseBetween(ListNode head, int m, int n) {
        if (m == n) return head;
        ListNode resultList = new ListNode(0);
        resultList.next = head;
        for (int i = 1; i < m; i++) {
          resultList = resultList.next;
        }
        ListNode p = resultList.next;
        ListNode pNext = p.next;
        for (int i = m; i < n; i++) {
          p.next = pNext.next;
          pNext.next = resultList.next;
          resultList.next = pNext;
          pNext = p.next;
        }
        if (m == 1)
          return resultList.next;
        else
          return head;
        }
}
```

> 复杂度分析

for遍历了一遍链表到n，时间复杂度O(n)

额外使用起始指针和前后指针，三个指针变量,空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Reverse Linked List II.
Memory Usage: 39.5 MB, less than 11.36% of Java online submissions for Reverse Linked List II.
