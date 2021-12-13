### LeetCode-563-binary-tree-tilt

> 题目链接

[LeetCode-563-binary-tree-tilt](https://leetcode-cn.com/problems/binary-tree-tilt/)

> 思路

遍历树结构，不断返回总和，计算获取坡度

> 代码

```java
class Solution {
    private int height = 0;
    public int findTilt(TreeNode root) {
        getHeight(root);
        return height;
    }
    public int getHeight(TreeNode root){
        if(root == null) return 0;
        int left = getHeight(root.left);
        int right = getHeight(root.right);
        height += Math.abs(left - right);
        return root.val + left + right;
    }
}
```

> 复杂度分析

利用排序，再遍历，时间复杂度O(n)

额外使用h的函数栈，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了98.14%的用户
