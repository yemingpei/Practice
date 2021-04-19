### LeetCode-offer-36

> 题目链接

[LeetCode-offer-36](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

> 思路

中序遍历，在根的地方链接前后节点，中序遍历是二叉树的顺序输出

> 代码

```java
class Solution {
    Node pre, head;
    public Node treeToDoublyList(Node root) {
        if(root == null) return null;
        dfs(root);
        head.left = pre;
        pre.right = head;
        return head;
    }
    void dfs(Node cur) {
        if(cur == null) return;
        dfs(cur.left);
        if(pre != null) pre.right = cur;
        else head = cur;
        cur.left = pre;
        pre = cur;
        dfs(cur.right);
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.5 MB, 在所有 Java 提交中击败了97.57%的用户
