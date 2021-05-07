### LeetCode-offer-55-I

> 题目链接

[LeetCode-offer-55-I](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

> 思路

遍历左右子树，然后取大的层数再加上1，就是高度

> 代码

```java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

函数调用栈为树的深度，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了83.16%的用户
