### LeetCode-offer-07

> 题目链接

[LeetCode-offer-07](https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof//)

> 思路

pre来表示现在到哪一个根节点，中序遍历，必然先产生根节点，in表示左子树已经就绪

> 代码

```java
class Solution {
    private int in = 0;
    private int pre = 0;
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return build(preorder, inorder, Integer.MIN_VALUE);
    }
    public TreeNode build(int[] preorder, int[] inorder, int stopFlag) {
        if (pre >= preorder.length) {
            return null;
        }
        if (inorder[in] == stopFlag) {
            in++;
            return null;
        }
        TreeNode root = new TreeNode(preorder[pre++]);
        root.left = build(preorder, inorder, root.val);
        root.right = build(preorder, inorder, stopFlag);
        return root;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了75.55%的用户

