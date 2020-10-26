### LeetCode-237-Delete-Node-in-a-Linked-List

> 题目链接

[LeetCode-237-Delete-Node-in-a-Linked-List](https://leetcode.com/problems/delete-node-in-a-linked-list/)

> 思路

分情况处理，如果在链表中间，直接复制next和指向next的next

> 代码

```java
class Solution {
    public void deleteNode(ListNode node) {
        if(node == null) return;
        if(node.next == null){
            node = null;
            return;
        }
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

> 复杂度分析

裁剪当前链表，时间复杂度O(1)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Delete Node in a Linked List.

Memory Usage: 38.8 MB, less than 11.96% of Java online submissions for Delete Node in a Linked List.
