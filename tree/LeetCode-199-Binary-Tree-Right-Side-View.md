### LeetCode-199-Binary-Tree-Right-Side-View

> 题目链接

[LeetCode-199-Binary-Tree-Right-Side-View](https://leetcode.com/problems/binary-tree-right-side-view/)

> 思路

使用递归，先递归右子树，找出该层最右边的数

> 代码

```java
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new LinkedList<> ();
        visitNode(root, result, 0);
        return result;
    }
    
    public void visitNode(TreeNode node, List<Integer> result, int depth) {
        if (node == null) return;
        if (depth == result.size()) {
            result.add(node.val);
        }
        visitNode(node.right, result, depth+1);
        visitNode(node.left, result, depth+1);
    }
}
```

> 复杂度分析

需要遍历树的元素识别是否是该层，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Binary Tree Right Side View.

Memory Usage: 39.3 MB, less than 25.38% of Java online submissions for Binary Tree Right Side View.
