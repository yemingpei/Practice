### LeetCode-530-minimum-absolute-difference-in-bst

> 题目链接

[LeetCode-530-minimum-absolute-difference-in-bst](https://leetcode-cn.com/problems/minimum-absolute-difference-in-bst/)

> 思路

中序遍历，不断计算差值，对比获取最小的值

> 代码

```java
class Solution {
    int pre;
    int ans;
    public int getMinimumDifference(TreeNode root) {
        ans = Integer.MAX_VALUE;
        pre = -1;
        dfs(root);
        return ans;
    }
    public void dfs(TreeNode root) {
        if (root == null) {
            return;
        }
        dfs(root.left);
        if (pre == -1) {
            pre = root.val;
        } else {
            ans = Math.min(ans, root.val - pre);
            pre = root.val;
        }
        dfs(root.right);
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用栈空间，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了66.59%的用户
