### LeetCode-257-Binary-Tree-Paths

> 题目链接

[LeetCode-257-Binary-Tree-Paths](https://leetcode.com/problems/binary-tree-paths/)

> 思路

回溯法，寻找叶子节点

> 代码

```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();
        if(root != null) createString(result, new StringBuilder(), root);
        return result;
    }
    public void createString(List<String> list, StringBuilder text, TreeNode root){
        int length = text.length();
        if(length > 0)
            text.append("->");
        text.append(root.val);
        if(root.left == null && root.right == null){
            list.add(text.toString());
        }else{
            if(root.left != null) createString(list, text, root.left);
            if(root.right != null) createString(list, text, root.right);
        }
        text.setLength(length);
    }
}
```

> 复杂度分析

需要遍历树的元素，时间复杂度O(n)

额外StringBuild来保存字串，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.97% of Java online submissions for Binary Tree Paths.

Memory Usage: 39.6 MB, less than 38.24% of Java online submissions for Binary Tree Paths.
