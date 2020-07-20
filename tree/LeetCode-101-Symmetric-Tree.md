### LeetCode-101-Symmetric-Tree

> 题目链接

[LeetCode-101-Symmetric-Tree](https://leetcode.com/problems/symmetric-tree/)

> 思路

比较节点是否相等，相等则继续比较子节点的情况，isSame(first.left, second.right)&&isSame(first.right, second.left)是关键

> 代码

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root == null) return true;
        return isSame(root.left, root.right);
    }
    public boolean isSame(TreeNode first, TreeNode second){
        if(first == null && second == null) return true;
        if(first != null && second == null) return false;
        if(first == null && second != null) return false;
        if(first.val != second.val) return false;
        return isSame(first.left, second.right)&&isSame(first.right, second.left);
    }
}
```

> 复杂度分析

遍历整棵树，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Symmetric Tree.

Memory Usage: 38 MB, less than 37.19% of Java online submissions for Symmetric Tree.
