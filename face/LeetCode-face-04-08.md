### LeetCode-face-04-08

> 题目链接

[LeetCode-face-04-08](https://leetcode-cn.com/problems/first-common-ancestor-lcci/)

> 思路

寻找节点的公共父亲节点，就会有两种情况，一种是两个节点分别分布在左右，第二种就是其中一个就是父节点

> 代码

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null) return null;
        if(root == p || root == q) return root;
        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);
        if(left != null && right != null) return root;
        if(left != null) return left;
        if(right != null) return right;
        return null;
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：7 ms, 在所有 Java 提交中击败了99.72%的用户

内存消耗：40.7 MB, 在所有 Java 提交中击败了31.51%的用户
