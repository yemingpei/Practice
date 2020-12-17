### LeetCode-337-House-Robber-III

> 题目链接

[LeetCode-337-House-Robber-III](https://leetcode.com/problems/house-robber-iii/)

> 思路

问题可以拆分为包含该点，和不包含该点，两个情况，包含该点时候，必然不包括子节点，不包含该点，则可以包括子节点。

> 代码

```java
class Solution {
    public int rob(TreeNode root) {
        int[] res = dp(root);
        return Math.max(res[0], res[1]);
    }
    private int[] dp(TreeNode root) {
        if (root == null) return new int[] {0, 0};
        int[] left = dp(root.left);
        int[] right = dp(root.right);
        int rob = root.val + left[0] + right[0];
        int not_rob = Math.max(left[1], left[0]) + Math.max(right[0], right[1]);
        return new int[]{not_rob, rob};
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

额外使用int数组来记录包含该点和不包含该点的数值，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for House Robber III.

Memory Usage: 41.4 MB, less than 5.00% of Java online submissions for House Robber III.
