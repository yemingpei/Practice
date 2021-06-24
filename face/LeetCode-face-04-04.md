### LeetCode-face-04-04

> 题目链接

[LeetCode-face-04-04](https://leetcode-cn.com/problems/check-balance-lcci/)

> 思路

从子节点开始比较，如果左右的高度相差大于1就返回-1，否则返回对应的高度

> 代码

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        return getHeight(root) != -1;
    }
    public int getHeight(TreeNode root){
        if(root == null) return 0;
        int left = getHeight(root.left);
        if(left == -1) return -1;
        int right = getHeight(root.right);
        if(right == -1) return -1;
        return Math.abs(left - right) > 1 ? -1 : Math.max(left, right) + 1;
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.5 MB, 在所有 Java 提交中击败了53.33%的用户
