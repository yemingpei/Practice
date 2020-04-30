### LeetCode-148-Sort-List

> 题目链接

[LeetCode-148-Sort-List](https://leetcode.com/problems/sort-list/)

> 思路

利用快慢指针分组，进行归并排序，然后再合并分组

> 代码

```java
class Solution {
    public ListNode sortList(ListNode head) {
		if (head == null || head.next == null)return head;
		ListNode node = null;
		ListNode low = head;
		ListNode fast = head;
		while (null != fast && null != fast.next) {
			node = low;
			low = low.next;
			fast = fast.next.next;
		}
		ListNode node1 = sortList(node.next);
		node.next = null;
		ListNode node2 = sortList(head);
		return mergeTwoLists(node1, node2);
	}

	private ListNode mergeTwoLists(ListNode first, ListNode last) {
		ListNode node1 = first;
		ListNode node2 = last;
		ListNode result = new ListNode(0);
		ListNode node = result;
		while (node1 != null || node2 != null) {
			if (node1 == null) {
				node.next = node2;
				node2 = node2.next;
			} else if (node2 == null) {
				node.next = node1;
				node1 = node1.next;
			} else if (node1.val > node2.val) {
				node.next = node2;
				node2 = node2.next;
			} else {
				node.next = node1;
				node1 = node1.next;
			}
			node = node.next;
		}
		return result.next;
	}
}
```

> 复杂度分析

归并排序，时间复杂度O(nlgn)

额外使用空间常数个指针，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 97.11% of Java online submissions for Sort List.
Memory Usage: 41.5 MB, less than 26.32% of Java online submissions for Sort List.
