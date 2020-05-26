### LeetCode-95-Unique-Binary-Search-Trees-II

> 题目链接

[LeetCode-95-Unique-Binary-Search-Trees-II](https://leetcode.com/problems/unique-binary-search-trees-ii/)

> 思路

二叉搜索树，因为是全排列，先确定根，然后小的在左边，大的在右边，小的依次为左子树，大的依次为右子树，此亦为递归公式。

> 代码

```java
class Solution {
    public List<TreeNode> generateTrees(int n) {
      if (n == 0) return new ArrayList<>();
      return bringTree(1, n);
	}

	public List<TreeNode> bringTree(int left, int right) {
      List<TreeNode> list = new ArrayList<>();
      if (left > right) list.add(null);
      for (int i = left; i <= right; i++) {
        List<TreeNode> leftList = bringTree(left, i - 1);
        List<TreeNode> rightList = bringTree(i + 1, right);
        for (TreeNode leftNode : leftList)
          for (TreeNode rightNode : rightList) {
            TreeNode node = new TreeNode(i);
            node.left = leftNode;
            node.right = rightNode;
            list.add(node);
          }
      }
      return list;
	}
}
```

> 复杂度分析

全排列问题，时间复杂度O(n!)

无使用额外空间，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 95.76% of Java online submissions for Unique Binary Search Trees II.

Memory Usage: 40.2 MB, less than 40.47% of Java online submissions for Unique Binary Search Trees II.
