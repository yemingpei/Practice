### LeetCode-112-Path-Sum

> 题目链接

[LeetCode-112-Path-Sum](https://leetcode.com/problems/path-sum/)

> 思路

没有左右子树的节点是叶子结点，比较路径的和是否相等

> 代码

```java
class Solution {
    public boolean hasPathSum(TreeNode root, int sum) {
        if(root == null) return false;
        return checkPath(root, sum, 0);
    }
    public boolean checkPath(TreeNode root, int target, int sum){
        if(root.left == null && root.right == null) return target == (sum + root.val);
        return (root.left != null && checkPath(root.left, target, sum + root.val)) ||
            (root.right != null && checkPath(root.right, target, sum + root.val));
    }
}
```

> 复杂度分析

寻找叶子节点，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Path Sum.

Memory Usage: 39.6 MB, less than 11.07% of Java online submissions for Path Sum.
