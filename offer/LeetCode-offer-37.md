### LeetCode-offer-37

> 题目链接

[LeetCode-offer-37](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)

> 思路

前序遍历，先保存好树的内容，然后再分割字符串，拼接回来

> 代码

```java
public class Codec {
    StringBuilder build = new StringBuilder();
    int index;
    public String serialize(TreeNode root) {
        dfs(root);
        return build.toString();
    }
    public void dfs(TreeNode root) {
        if (root == null) {
            if (build.length() != 0) build.append(",");
            build.append("null");
            return;
        }
        if (build.length() != 0) build.append(",");
        build.append(String.valueOf(root.val));
        dfs(root.left);
        dfs(root.right);
    }
    public TreeNode deserialize(String data) {
        String[] treeNodes = data.split(",");
        index = 0;
        return buildTree(treeNodes);
    }
    public TreeNode buildTree(String[] treeNodes) {
        if (treeNodes[index].equals("null")) return null;
        TreeNode tree = new TreeNode(Integer.valueOf(treeNodes[index]));
        if (++index < treeNodes.length) tree.left = buildTree(treeNodes);
        if (++index < treeNodes.length) tree.right = buildTree(treeNodes);
        return tree;
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

无额外使用StringBuilder，空间复杂度O(1)

> 总结

执行用时：11 ms, 在所有 Java 提交中击败了91.62%的用户

内存消耗：40.2 MB, 在所有 Java 提交中击败了78.47%的用户
