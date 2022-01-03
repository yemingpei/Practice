### LeetCode-606-construct-string-from-binary-tree

> 题目链接

[LeetCode-606-construct-string-from-binary-tree](https://leetcode-cn.com/problems/construct-string-from-binary-tree/)

> 思路

前序遍历树，拼接字符串

> 代码

```java
class Solution {
    StringBuilder sb = new StringBuilder();
    public String tree2str(TreeNode root) {
        if (root == null) return "";
        preOrder(root);
        return sb.toString();
    }
    private void preOrder(TreeNode root) {
        if (root == null) return;
        sb.append(root.val);
        if (root.left != null) {
            sb.append("(");
            preOrder(root.left);
            sb.append(")");
        }else {
            if (root.right != null) sb.append("()");
        }
        if (root.right != null) {
            sb.append("(");
            preOrder(root.right);
            sb.append(")");
        }
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用函数栈空间来递归，空间复杂度O(h)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了88.58%的用户
