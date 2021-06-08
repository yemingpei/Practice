### LeetCode-face-02-03

> 题目链接

[LeetCode-face-02-03](https://leetcode-cn.com/problems/delete-middle-node-lcci/)

> 思路

用节点的下一个节点来代替，然后剔除下一个节点完成节点的移除

> 代码

```java
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

> 复杂度分析

截断链表，再拼接，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.5 MB, 在所有 Java 提交中击败了96.40%的用户
