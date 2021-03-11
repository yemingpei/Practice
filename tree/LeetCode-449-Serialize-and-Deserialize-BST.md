### LeetCode-449-Serialize-and-Deserialize-BST

> 题目链接

[LeetCode-449-Serialize-and-Deserialize-BST](https://leetcode.com/problems/serialize-and-deserialize-bst/)

> 思路

树转换成String，中序遍历，String转换成树，后序遍历

> 代码

```java
public class Codec {
    int index = 0;
    public String serialize(TreeNode root) {   
        StringBuilder sb = new StringBuilder();
        serialize(root, sb);
        return sb.toString();
    }
    private void serialize(TreeNode root, StringBuilder sb) {
        if (root == null) return;
        sb.append((char) (root.val));
        serialize(root.left, sb);
        serialize(root.right, sb);
    }
    public TreeNode deserialize(String data) {
        index = 0;
        return deserialize(data, Integer.MIN_VALUE, Integer.MAX_VALUE);
    }
    public TreeNode deserialize(String data, int min, int max) {
        if (index == data.length()) return null;
        int x = (int)data.charAt(index);
        if (x < min || x> max) return null;
        index++;
        TreeNode node = new TreeNode(x);
        node.left = deserialize(data, min, x);
        node.right = deserialize(data, x, max);
        return node;
    }
}
```

> 复杂度分析

遍历字符串和节点，时间复杂度O(n)

额外使用Node来保存，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.89% of Java online submissions for Serialize and Deserialize BST.

Memory Usage: 39.6 MB, less than 89.22% of Java online submissions for Serialize and Deserialize BST.
