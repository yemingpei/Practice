### LeetCode-99-Recover-Binary-Search-Tree

> 题目链接

[LeetCode-99-Recover-Binary-Search-Tree](https://leetcode.com/problems/recover-binary-search-tree/)

> 思路

二叉搜索树符合中序遍历是递增数列，如果出现错误的点，必然存在递减的节点，中序遍历，记录递减的点，再寻找后面比它小的节点的最大点，交换就可以

> 代码

```java
class Solution {
  TreeNode first;
  TreeNode second;
  boolean lock;

  public void recoverTree(TreeNode root) {
      compareNumber(root);
      int number = first.val;
      first.val = second.val;
      second.val = number;
  }

  public void compareNumber(TreeNode node) {
      if (node == null) return;
      compareNumber(node.left);
      if (!lock && (first == null || node.val > first.val)) first = node;
      else if (lock && first.val < node.val) return;
      else {
        lock = true;
        second = node;
      }
      compareNumber(node.right);
   }
}
```

> 复杂度分析

中序遍历树，时间复杂度O(n)

额外使用了两个指针记录交换的点和一个boolean的flag，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Recover Binary Search Tree.

Memory Usage: 39.6 MB, less than 80.77% of Java online submissions for Recover Binary Search Tree.
