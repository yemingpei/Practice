### LeetCode-offer-68-II

> 题目链接

[LeetCode-offer-68-II](https://leetcode-cn.com/problems/er-cha-shu-de-zui-jin-gong-gong-zu-xian-lcof/)

> 思路

搜索左右子树，如果左右子树分别返回当前结点就是公共节点，否则就用最后一个出线的节点覆盖

> 代码

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null) return null;
        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);
        if(left != null && right != null) return root;
        if(root.val == p.val || root.val == q.val) return root;
        if(left != null) return left;
        if(right != null) return right;
        return null;
    }
}
```

> 复杂度分析

遍历了树，时间复杂度O(n)

递归，函数栈，空间复杂度O(logn)

> 总结

执行用时：7 ms, 在所有 Java 提交中击败了99.98%的用户

内存消耗：39.7 MB, 在所有 Java 提交中击败了73.97%的用户
