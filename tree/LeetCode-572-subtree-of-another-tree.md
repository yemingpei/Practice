### LeetCode-572-subtree-of-another-tree

> 题目链接

[LeetCode-572-subtree-of-another-tree](https://leetcode-cn.com/problems/subtree-of-another-tree/)

> 思路

不断遍历，循环比较每个节点是否相同

> 代码

```java
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(subRoot == null) return true;
        if(root == null) return false;
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot) || method(root, subRoot);
    }
    boolean method(TreeNode r, TreeNode s){
        if(r == null && s == null) return true;
        if(r == null || s == null) return false;
        if(r.val != s.val) return false;
        return method(r.left, s.left) && method(r.right, s.right);
    }
}
```

> 复杂度分析

遍历两个树，时间复杂度O(nm)

额外使用树的高度的函数栈，空间复杂度O(h)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.92%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了89.58%的用户
