### LeetCode-235-Lowest-Common-Ancestor-of-a-Binary-Search-Tree

> 题目链接

[LeetCode-235-Lowest-Common-Ancestor-of-a-Binary-Search-Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

> 思路

最小公共子节点，化解为子问题，树的左右字数分别包含目标节点，或者其中一个节点为根，另一个在子数内,未剪枝，可以继续剪枝优化

> 代码

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null || root == p || root == q) return root;
        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);
        if(left != null && right != null) return root;
        return left == null ? right : left;
    }
}
```

> 复杂度分析

树，找到结果直接返回，时间复杂度O(n)

递归栈为树的高度，空间复杂度O(H)

> 总结

Runtime: 4 ms, faster than 56.59% of Java online submissions for Lowest Common Ancestor of a Binary Search Tree.

Memory Usage: 39.5 MB, less than 5.31% of Java online submissions for Lowest Common Ancestor of a Binary Search Tree.
