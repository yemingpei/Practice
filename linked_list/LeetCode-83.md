### LeetCode-83-Remove-Duplicates-from-Sorted-List

> 题目链接

[LeetCode-83-Remove-Duplicates-from-Sorted-List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

> 思路

链表，不相同就跳过，相同则指向相同元素的下个节点

> 代码

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode p = head;
		while (p != null && p.next != null) {
			if (p.val < p.next.val) {
				p = p.next;
			} else {
				p.next = p.next.next;
			}
		}
		return head;
    }
}
```

> 复杂度分析

遍历了一遍链表，时间复杂度O(n)

额外使用了1个链表元素,空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Remove Duplicates from Sorted List.
Memory Usage: 39.1 MB, less than 7.14% of Java online submissions for Remove Duplicates from Sorted List.
