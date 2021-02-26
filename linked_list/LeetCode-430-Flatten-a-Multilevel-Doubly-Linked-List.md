### LeetCode-430-Flatten-a-Multilevel-Doubly-Linked-List

> 题目链接

[LeetCode-430-Flatten-a-Multilevel-Doubly-Linked-List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)

> 思路

深度链表，先解掉child的链接，递归结束，再回来拼接前后节点信息

> 代码

```java
class Solution {
    public Node flatten(Node head) {
        if (head == null) return head;
        Node pseudoHead = new Node(0, null, head, null);
        flattenDFS(pseudoHead, head);
        pseudoHead.next.prev = null;
        return pseudoHead.next;
    }
    public Node flattenDFS(Node prev, Node curr) {
        if (curr == null) return prev;
        curr.prev = prev;
        prev.next = curr;
        Node tempNext = curr.next;
        Node tail = flattenDFS(curr, curr.child);
        curr.child = null;
        return flattenDFS(tail, tempNext);
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

无使用额外变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Flatten a Multilevel Doubly Linked List.

Memory Usage: 37.1 MB, less than 62.95% of Java online submissions for Flatten a Multilevel Doubly Linked List.
