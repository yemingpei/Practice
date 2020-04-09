### LeetCode-86-Partition-List

> 题目链接

[LeetCode-86-Partition-List](https://leetcode.com/problems/partition-list/)

> 思路

先找到第一个不小于x的值，作为插入点，然后再分割点后面找小于x的值，插入到插入点的位置

> 代码

```java
class Solution {
    public ListNode partition(ListNode head, int x) {
        if (head == null || head.next == null) return head;
		ListNode resultList = new ListNode(0);
		resultList.next = head;
		ListNode first = resultList;
		while (first.next != null && first.next.val < x) {
			first = first.next;
		}
		if (first.next == null) return head;
		ListNode end = first.next;
		while (end != null && end.next != null) {
			if (end.next.val < x) {
				ListNode tmp = end.next;
				end.next = tmp.next;
				tmp.next = first.next;
				first.next = tmp;
				first = first.next;
			} else {
				end = end.next;
			}
		}
		return resultList.next;
    }
}
```

> 复杂度分析

从头到尾遍历了一次链表，时间复杂度O(n)

额外使用了4个指针变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Partition List.
Memory Usage: 38.7 MB, less than 5.77% of Java online submissions for Partition List.
