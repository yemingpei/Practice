### LeetCode-offer-55-II

> 题目链接

[LeetCode-offer-55-II](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

> 思路

遍历左右子树，然后取大的层数再加上1，就是高度，不满足，提前剪枝，返回-1

> 代码

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        return treeDfs(root) != -1;
    }

    public int treeDfs(TreeNode root){
        if(root == null) return 0;
        int left = treeDfs(root.left);
        if(left == -1) return -1;
        int right = treeDfs(root.right);
        if(right == -1) return -1;
        return Math.abs(left - right) > 1 ? -1 : Math.max(left, right) + 1;
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

函数调用栈为树的深度，空间复杂度O(logn)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了83.16%的用户
