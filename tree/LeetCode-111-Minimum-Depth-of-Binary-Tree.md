### LeetCode-111-Minimum-Depth-of-Binary-Tree

> 题目链接

[LeetCode-111-Minimum-Depth-of-Binary-Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

> 思路

后序遍历树，输出每个子树的最小高度，递归得到整个树的最小高度

> 代码

```java
class Solution {
    public int minDepth(TreeNode root) {
        if(root == null) return 0;
        if(root.left ==null && root.right == null) return 1;
        int left = minDepth(root.left);
        int right = minDepth(root.right);
        return Math.min(left == 0 ?Integer.MAX_VALUE:left,right == 0 ?Integer.MAX_VALUE:right) + 1;
    }
}
```

> 复杂度分析

遍历整棵树，时间复杂度O(n)

无额外使用辅助空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Minimum Depth of Binary Tree.

Memory Usage: 39.9 MB, less than 70.31% of Java online submissions for Minimum Depth of Binary Tree.
