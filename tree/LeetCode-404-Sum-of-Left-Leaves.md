### LeetCode-404-Sum-of-Left-Leaves

> 题目链接

[LeetCode-404-Sum-of-Left-Leaves](https://leetcode.com/problems/sum-of-left-leaves/)

> 思路

遍历树寻找左叶子节点，然后返回左叶子节点之和

> 代码

```java
class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        return root != null ? dfs(root) : 0;
    }
    public int dfs(TreeNode node) {
        int ans = 0;
        if (node.left != null) {
            ans += isLeafNode(node.left) ? node.left.val : dfs(node.left);
        }
        if (node.right != null && !isLeafNode(node.right)) {
            ans += dfs(node.right);
        }
        return ans;
    }
    public boolean isLeafNode(TreeNode node) {
        return node.left == null && node.right == null;
    }
}
```

> 复杂度分析

需要遍历树的元素，时间复杂度O(n)

递归深度，空间复杂度O(logn)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Sum of Left Leaves.

Memory Usage: 36.5 MB, less than 88.73% of Java online submissions for Sum of Left Leaves.
