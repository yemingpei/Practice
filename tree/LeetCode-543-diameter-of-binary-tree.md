### LeetCode-543-diameter-of-binary-tree

> 题目链接

[LeetCode-543-diameter-of-binary-tree](https://leetcode-cn.com/problems/diameter-of-binary-tree/)

> 思路

递归统计树的直径

> 代码

```java
class Solution {
    int max = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        diameterOfSingleTree(root);
        return max;
    }
    public int diameterOfSingleTree(TreeNode root){
        if(root == null) return 0;
        int left = diameterOfSingleTree(root.left);
        int right = diameterOfSingleTree(root.right);
        max = Math.max(max, left + right);
        return Math.max(left, right) + 1;
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用树的深度的栈空间，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了77.64%的用户
