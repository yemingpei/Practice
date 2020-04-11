### LeetCode-142-Linked-List-Cycle-II

> 题目链接

[LeetCode-142-Linked-List-Cycle-II](https://leetcode.com/problems/linked-list-cycle-ii/)

> 思路

快慢指针同时出发，快指针走两步，慢指针，走一步，如果快指针追上慢指针，则证明有环。相遇点肯定在环上，而且慢指针没有走完一圈环

出发点到入口点的距离为d，入口点和相遇点的距离为x，环的长度为r，则有慢指针走的距离S = d+x，快指针的距离则为2S = d + n * r + x（出发点走到入口点，然后转了n圈回到入口点，再走到相遇点，相遇）。
则有2S - S  = n * r,则有 S = n * r.如果此时又又一个慢指针从头部走出，走了S的距离，正好到相遇点，慢指针从相遇点出发，走S距离，则也回到相遇点，往前推就是在相遇点就开始重合，一步一步走过来

> 代码

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode low = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
          low = low.next;
          fast = fast.next.next;
          if (fast == low) {
            while (head != low) {
              head = head.next;
              low = low.next;
            }
                    return head;
          }
        }
        return null;
    }
}
```

> 复杂度分析

快指针走了 2S距离，慢指针走了2S- x 头指针走了S -x ,总距离走了5S -2x，S少于链表的长度 ，x小于环的长度，时间复杂度O(n)

额外使用了快慢指针，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Linked List Cycle II.
Memory Usage: 39.7 MB, less than 6.32% of Java online submissions for Linked List Cycle II.
