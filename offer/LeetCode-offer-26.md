### LeetCode-offer-26

> 题目链接

[LeetCode-offer-26](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

> 思路

树节点比较，一边查找头节点，然后再循环比较

> 代码

```java
class Solution {
    public boolean isSubStructure(TreeNode A, TreeNode B) {
        if(A == null || B == null) return false;
        return recur(A, B) || isSubStructure(A.left, B) || recur(A.right, B);
    }

    public boolean recur(TreeNode A, TreeNode B){
        if(B == null) return true;
        if(A == null) return false;
        return (A.val == B.val) && recur(A.left, B.left) && recur(A.right, B.right); 
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：40.3 MB, 在所有 Java 提交中击败了39.15%的用户
