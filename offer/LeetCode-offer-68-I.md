### LeetCode-offer-68-I

> 题目链接

[LeetCode-offer-68-I](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-zui-jin-gong-gong-zu-xian-lcof/)

> 思路

利用二叉搜索树的大小规则，如果root节点都比p和q大，则在左子树寻找，如果root节点都比p和q小，则在右子树寻找，否则就是当前节点。

> 代码

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(p.val > q.val) return lowestCommonAncestorOrder(root, q, p);
        else return lowestCommonAncestorOrder(root, p, q);
    }

    public TreeNode lowestCommonAncestorOrder(TreeNode root, TreeNode low, TreeNode high) {
        if(root.val < low.val) return lowestCommonAncestorOrder(root.right, low, high);
        if(root.val > high.val) return lowestCommonAncestorOrder(root.left, low, high);
        if(root.val == low.val) return low;
        if(root.val == high.val) return high;
        return root;
    }
}
```

> 复杂度分析

遍历了树，时间复杂度O(n)

递归，函数栈，空间复杂度O(logn)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了87.15%的用户
