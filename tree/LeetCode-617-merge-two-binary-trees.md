### LeetCode-617-merge-two-binary-trees

> 题目链接

[LeetCode-617-merge-two-binary-trees](https://leetcode-cn.com/problems/merge-two-binary-trees/)

> 思路

遍历树，重组树的结构，合并到root1

> 代码

```java
class Solution {
    public TreeNode mergeTrees(TreeNode root1, TreeNode root2) {
        if(root1 == null) return root2;
        if(root2 == null) return root1;
        root1.val += root2.val;
        root1.left = mergeTrees(root1.left, root2.left);
        root1.right = mergeTrees(root1.right, root2.right);
        return root1;
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用函数栈空间来递归，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.7 MB, 在所有 Java 提交中击败了34.49%的用户
