### LeetCode-513-find-bottom-left-tree-value

> 题目链接

[LeetCode-513-find-bottom-left-tree-value](https://leetcode-cn.com/problems/find-bottom-left-tree-value/)

> 思路

后根遍历，根据层数来记录节点的值

> 代码

```java
class Solution {
    private int left;
    private int height = -1;
    public int findBottomLeftValue(TreeNode root) {
        searchNode(root, 0);
        return left;
    }
    public void searchNode(TreeNode root, int i){
        if(root.left != null) searchNode(root.left, i + 1);
        if(root.right != null) searchNode(root.right, i + 1);
        if(height < i){
            height = i;
            left = root.val;
        }
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用递归栈，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.9 MB, 在所有 Java 提交中击败了82.13%的用户
