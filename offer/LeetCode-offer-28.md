### LeetCode-offer-28

> 题目链接

[LeetCode-offer-28](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

> 思路

比较两个节点是否相等，相等则比较两个节点的左节点和右节点

> 代码

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root == null) return true;
        return checkTree(root.left, root.right);
    }
    public boolean checkTree(TreeNode node1, TreeNode node2){
        if(node1 == null && node2 ==null) return true;
        if(node1 == null) return false;
        if(node2 == null) return false;
        if(node1.val != node2.val) return false;
        return checkTree(node1.left, node2.right) && checkTree(node1.right, node2.left);
    }
}
```

> 复杂度分析

交叉比较树的节点，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.3 MB, 在所有 Java 提交中击败了80.69%的用户
