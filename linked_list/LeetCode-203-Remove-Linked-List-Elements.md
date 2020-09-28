### LeetCode-203-Remove-Linked-List-Elements

> 题目链接

[LeetCode-203-Remove-Linked-List-Elements](https://leetcode.com/problems/remove-linked-list-elements/)

> 思路

比较每个节点的val，如果相同，则跳过，指向他的下一个节点

> 代码

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode root = new ListNode();
        root.next = head;
        ListNode node = root;
        while(node.next != null){
            if(node.next.val == val){
                node.next = node.next.next;
            }else{
                node = node.next;
            }
        }
        return root.next;
    }
}
```

> 复杂度分析

遍历整个链表，时间复杂度O(n)

额外使用两个node，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 88.25% of Java online submissions for Remove Linked List Elements.

Memory Usage: 40 MB, less than 98.20% of Java online submissions for Remove Linked List Elements.
