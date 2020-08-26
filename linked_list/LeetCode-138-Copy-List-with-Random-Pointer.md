### LeetCode-138-Copy-List-with-Random-Pointer

> 题目链接

[LeetCode-138-Copy-List-with-Random-Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

> 思路

用map记录已经构建的节点，以此作为跳出判断的依据，避免死循环。

> 代码

```java
class Solution {
    public Node copyRandomList(Node head) {
        Map<Node, Node> map = new HashMap<>();
        return getNode(head, map);
    }
    public Node getNode(Node head, Map<Node, Node> map){
        if(head == null) return null;
        if(map.containsKey(head)) return map.get(head);
        Node node = new Node(head.val);
        map.put(head, node);
        node.next = getNode(head.next, map);
        node.random = getNode(head.random, map);
        return node;
    }
}
```

> 复杂度分析

遍历整个链表，时间复杂度O(n)

额外使用map来记录指针，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Copy List with Random Pointer.

Memory Usage: 39.1 MB, less than 78.30% of Java online submissions for Copy List with Random Pointer.
