### LeetCode-offer-25

> 题目链接

[LeetCode-offer-25](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

> 思路

比较两个链表的头，来决定拼哪一个节点，其中一个链表遍历完时，直接拼接剩下的节点

> 代码

```java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0);
        ListNode node = head;
        while(l1 != null && l2 != null){
            if(l2.val > l1.val){
                node.next = l1;
                node = node.next;
                l1 = l1.next;
            }else{
                node.next = l2;
                node = node.next;
                l2 = l2.next;
            }
        }
        if(l1 != null) node.next = l1;
        if(l2 != null) node.next = l2;
        return head.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n + m)

额外使用1个指针，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.67%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了87.95%的用户
