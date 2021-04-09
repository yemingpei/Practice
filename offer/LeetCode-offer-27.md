### LeetCode-offer-27

> 题目链接

[LeetCode-offer-27](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

> 思路

递归交换树的节点，不断变换左右节点

> 代码

```java
class Solution {
    public TreeNode mirrorTree(TreeNode root) {
        changeTree(root);
        return root;
    }
    public void changeTree(TreeNode node){
        if(node == null) return;
        TreeNode right = node.right;
        node.right = node.left;
        node.left = right;
        changeTree(node.right);
        changeTree(node.left);
    }
}
```

> 复杂度分析

交换树的节点，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.5 MB, 在所有 Java 提交中击败了97.99%的用户
