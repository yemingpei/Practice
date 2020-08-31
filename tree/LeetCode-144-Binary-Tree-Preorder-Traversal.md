### LeetCode-144-Binary-Tree-Preorder-Traversal

> 题目链接

[LeetCode-144-Binary-Tree-Preorder-Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)

> 思路

前序遍历，先输出根，然后是左子树，接着右子树

> 代码

```java
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        addRootNode(list, root);
        return list;
    }
    public void addRootNode(List<Integer> list, TreeNode root){
        if(root == null) return;
        list.add(root.val);
        addRootNode(list, root.left);
        addRootNode(list, root.right);
    }
}
```

> 复杂度分析

需要遍历树的元素比较，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Binary Tree Preorder Traversal.

Memory Usage: 38 MB, less than 47.14% of Java online submissions for Binary Tree Preorder Traversal.
