### LeetCode-offer-54

> 题目链接

[LeetCode-offer-54](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

> 思路

先遍历右子树，然后是根，最后是左子树，到k的时候，后续都剪枝。

> 代码

```java
class Solution {
    public int count = 0;
    public int number;
    public int kthLargest(TreeNode root, int k) {
        searchK(root, k);
        return number;
    }
    public void searchK(TreeNode root, int k){
        if(root.right != null) searchK(root.right, k);
        count++;
        if(count == k) {
            number = root.val;
            return;
        }
        if(count > k) return;
        if(root.left != null) searchK(root.left, k);
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

函数调用栈为树的深度，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了58.55%的用户
