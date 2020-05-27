### LeetCode-98-Validate-Binary-Search-Tree

> 题目链接

[LeetCode-98-Validate-Binary-Search-Tree](https://leetcode.com/problems/validate-binary-search-tree/)

> 思路

二叉搜索树，满足根节点大于左子树的全部子节点，小于右子树的全部子节点，所以中序遍历，必然是递增数列。采用递归实现中序遍历，和前一个节点比较大小

> 代码

```java
class Solution {
    Integer number;
    public boolean isValidBST(TreeNode root) {
        return compareNumber(root);
    }
    
    public boolean compareNumber(TreeNode node){
        if(node == null) return true;
        boolean left = compareNumber(node.left);
        if(!left) return false; 
        if(number == null||node.val > number) number = node.val;
        else return false;
        return compareNumber(node.right);
    }
}
```

> 复杂度分析

需要循环遍历树，时间复杂度O(n)

额外使用int空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Validate Binary Search Tree.

Memory Usage: 39.5 MB, less than 79.54% of Java online submissions for Validate Binary Search Tree.
