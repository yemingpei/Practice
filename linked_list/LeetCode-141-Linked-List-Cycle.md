### LeetCode-141-Linked-List-Cycle

> 题目链接

[LeetCode-141-Linked-List-Cycle](https://leetcode.com/problems/linked-list-cycle/)

> 思路

快慢指针，如果快指针追上慢指针，则说明有环，如果快指针先到达尾部null，则没有环

> 代码

```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode low = head;
		ListNode fast = head;
		while (fast != null && fast.next != null) {
			low = low.next;
			fast = fast.next.next;
			if (fast == low)
				return true;
		}
		return false;
    }
}
```

> 复杂度分析

慢指针最远走完一轮链表，快指针则走了慢指针两倍的距离，总耗时应该是3n，时间复杂度O(n)

额外使用两个辅助指针，空间复杂度O(2)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Linked List Cycle.
Memory Usage: 39.8 MB, less than 5.71% of Java online submissions for Linked List Cycle.
