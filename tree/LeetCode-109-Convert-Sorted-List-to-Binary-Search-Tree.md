### LeetCode-109-Convert-Sorted-List-to-Binary-Search-Tree

> 题目链接

[LeetCode-109-Convert-Sorted-List-to-Binary-Search-Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

> 思路

思路同[LeetCode-108-Convert-Sorted-Array-to-Binary-Search-Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)，利用快慢指针来寻找中点。

> 代码

```java
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        if(head == null) return null;
        if(head.next == null) return new TreeNode(head.val);
        ListNode slow = head;
        ListNode fast = head;
        ListNode last = slow;
        while(fast != null && fast.next != null){
            last = slow;
            slow = slow.next;
            fast = fast.next.next;
        }
        last.next = null;
        return new TreeNode(slow.val, sortedListToBST(head), sortedListToBST(slow.next));
    }
}
```

> 复杂度分析

每个点都要遍历到，中间存在快慢子针，时间复杂度O(nlogn)

无额外使用空间，空间复杂度O(lgn)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Convert Sorted List to Binary Search Tree.

Memory Usage: 44.8 MB, less than 5.22% of Java online submissions for Convert Sorted List to Binary Search Tree.
