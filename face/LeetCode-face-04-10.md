### LeetCode-face-04-10

> 题目链接

[LeetCode-face-04-10](https://leetcode-cn.com/problems/check-subtree-lcci/)

> 思路

双重递归，先寻找是否有一样的根节点（起始节点），然后就是开始比较是否是一样的树

> 代码

```java
class Solution {
    public boolean checkSubTree(TreeNode t1, TreeNode t2) {
        if(t1 == null && t2 == null) return true;
        if(t1 == null || t2 == null) return false;
        if(t1.val == t2.val) return checkSameTree(t1, t2);
        return (checkSubTree(t1.left, t2) || checkSubTree(t1.right, t2));
    }
    public boolean checkSameTree(TreeNode t1, TreeNode t2){
        if(t1 == null && t2 == null) return true;
        if(t1 == null || t2 == null) return false;
        if(t1.val != t2.val) return false;
        return checkSameTree(t1.left, t2.left) && checkSameTree(t1.right, t2.right);
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.64%的用户

内存消耗：41.1 MB, 在所有 Java 提交中击败了85.04%的用户
