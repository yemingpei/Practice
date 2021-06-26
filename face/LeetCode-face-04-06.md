### LeetCode-face-04-06

> 题目链接

[LeetCode-face-04-06](https://leetcode-cn.com/problems/successor-lcci/)

> 思路

中序遍历，先找到节点P，然后改变全局的标志位，然后就可以输出下一个

> 代码

```java
class Solution {
    public boolean flag;
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        if(root == null) return null;
        if(root.left != null){
            TreeNode leftNode = inorderSuccessor(root.left, p);
            if(leftNode != null) return leftNode;
        }
        if(flag) return root;
        if(root == p) flag = true;
        if(root.right != null) {
            TreeNode rightNode = inorderSuccessor(root.right, p);
            if(rightNode != null) return rightNode;
        }
        return null;
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.2 MB, 在所有 Java 提交中击败了56.01%的用户
