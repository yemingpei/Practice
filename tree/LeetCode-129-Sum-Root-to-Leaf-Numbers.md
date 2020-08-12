### LeetCode-129-Sum-Root-to-Leaf-Numbers

> 题目链接

[LeetCode-129-Sum-Root-to-Leaf-Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

> 思路

从根节点开始不断往下遍历，计算每个分支的和，最后再相加

> 代码

```java
class Solution {
    public int sumNumbers(TreeNode root) {
        if(root == null) return 0;
        return getSum(root, 0);
        
    }
    public int getSum(TreeNode root, int count){
        int sum = count * 10 + root.val;
        if(root.left == null && root.right == null) return sum;
        int left = 0;
        int right = 0;
        if(root.left != null) left = getSum(root.left, sum);
        if(root.right != null) right = getSum(root.right, sum);
        return left + right;
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)，栈的是用深度为logn

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Sum Root to Leaf Numbers.

Memory Usage: 37.1 MB, less than 82.31% of Java online submissions for Sum Root to Leaf Numbers.
