### LeetCode-623-add-one-row-to-tree

> 题目链接

[LeetCode-623-add-one-row-to-tree](https://leetcode-cn.com/problems/add-one-row-to-tree/)

> 思路

遍历树，到达某一层的时候都插入指定节点

> 代码

```java
class Solution {
    public TreeNode addOneRow(TreeNode t, int v, int d) {
        if (d == 1) {
            TreeNode n = new TreeNode(v);
            n.left = t;
            return n;
        }
        insert(v, t, 1, d);
        return t;
    }

    public void insert(int val, TreeNode node, int depth, int n) {
        if (node == null)
            return;
        if (depth == n - 1) {
            TreeNode t = node.left;
            node.left = new TreeNode(val);
            node.left.left = t;
            t = node.right;
            node.right = new TreeNode(val);
            node.right.right = t;
        } else {
            insert(val, node.left, depth + 1, n);
            insert(val, node.right, depth + 1, n);
        }
    }
}
```

> 复杂度分析

遍历树的每个节点，时间复杂度O(n)

额外使用函数栈，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了35.46%的用户
