### LeetCode-110-Balanced-Binary-Tree

> 题目链接

[LeetCode-110-Balanced-Binary-Tree](https://leetcode.com/problems/balanced-binary-tree/)

> 思路

比较左右子树的高度，如果大于1，就返回false

> 代码

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        return countNode(root) >= 0;
    }
    private int countNode(TreeNode root){
        if(root == null) return 0;
        int left = countNode(root.left);
        int right = countNode(root.right);
        if(left < 0 || right < 0 || Math.abs(left - right) > 1) return -1;
        return Math.max(left, right) + 1;
    }
}
```

> 复杂度分析

最坏情况需要遍历整个数组，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Balanced Binary Tree.

Memory Usage: 39.4 MB, less than 70.41% of Java online submissions for Balanced Binary Tree.
