### LeetCode-100-Same-Tree

> 题目链接

[LeetCode-100-Same-Tree](https://leetcode.com/problems/same-tree/)

> 思路

遍历树比较是否相等

> 代码

```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) return true;
        if (p == null || q == null) return false;
        if (p.val != q.val) return false;
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

> 复杂度分析

需要遍历树的元素比较，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Same Tree.

Memory Usage: 36.9 MB, less than 5.75% of Java online submissions for Same Tree.
