### LeetCode-147-Insertion-Sort-List

> 题目链接

[LeetCode-147-Insertion-Sort-List](https://leetcode.com/problems/insertion-sort-list/)

> 思路

利用快慢指针分组，进行归并排序，然后再合并分组

> 代码

```java
class Solution {
    public ListNode insertionSortList(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode node = null;
        ListNode low = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
          node = low;
          low = low.next;
          fast = fast.next.next;
        }
        ListNode node1 = insertionSortList(node.next);
        node.next = null;
        ListNode node2 = insertionSortList(head);
        return mergeList(node1, node2);
    }
    public ListNode mergeList(ListNode first,ListNode second){
        ListNode node1 = first;
        ListNode node2 = second;
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

Runtime: 1 ms, faster than 99.76% of Java online submissions for Insertion Sort List.

Memory Usage: 39.6 MB, less than 45.58% of Java online submissions for Insertion Sort List.
