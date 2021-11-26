### LeetCode-538-convert-bst-to-greater-tree

> 题目链接

[LeetCode-538-convert-bst-to-greater-tree](https://leetcode-cn.com/problems/convert-bst-to-greater-tree/)

> 思路

遍历树，先右子树，然后根，接着左子树的顺序

> 代码

```java
class Solution {
    private int sum = 0;
    public TreeNode convertBST(TreeNode root) {
        if(root == null) return null;
        if(root.left == null && root.right == null){
            sum += root.val;
            root.val = sum;
        }else{
            convertBST(root.right);
            sum += root.val;
            root.val = sum;
            convertBST(root.left);
        }
        return root;
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

额外使用栈空间，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了64.19%的用户
