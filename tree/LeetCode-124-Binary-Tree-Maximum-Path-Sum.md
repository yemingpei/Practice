### LeetCode-124-Binary-Tree-Maximum-Path-Sum

> 题目链接

[LeetCode-124-Binary-Tree-Maximum-Path-Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

> 思路

后序遍历树，每次使用节点和最长左子树和最长右子树相加，然后和最大值比较。

> 代码

```java
class Solution {
    int max = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        int result = getMax(root);
        return Math.max(max,result);
    }
    
    public int getMax(TreeNode root){
        if (root == null) return 0;
        int left = Math.max(getMax(root.left), 0);
        int right = Math.max(getMax(root.right), 0);
        int number = root.val + left + right;
        max = Math.max(max, number);
        return root.val + Math.max(left,right);
    }
}
```

> 复杂度分析

后序遍历了整棵树树，时间复杂度O(n)

额外使用了一个int类型的max来辅助记录最大值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Binary Tree Maximum Path Sum.

Memory Usage: 41.3 MB, less than 9.52% of Java online submissions for Binary Tree Maximum Path Sum.
