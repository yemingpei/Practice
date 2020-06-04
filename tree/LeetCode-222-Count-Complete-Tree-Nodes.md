### LeetCode-222-Count-Complete-Tree-Nodes

> 题目链接

[LeetCode-222-Count-Complete-Tree-Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)

> 思路

```java
//例子1
  1
 2  3
4 5 6

//例子2
  1
 2  3
4 5
//例子3
 2
4 5
```
先求出数的深度，那么最后一层应该有最多2的depth次方个数，利用分治的方法实现递归，算最后一行的个数，一棵树取右子树的无限左节点，如果为空，则最后的
个数肯定在左边，如例子2，否则，在右边，如例子1，如果深度只剩下1的时候，如例子3，右子树没有，则输出1，否则是2

> 代码

```java
class Solution {
    public int countNodes(TreeNode root) {
      if (root == null) return 0;
      if (root.left == null) return 1;
      int depth = 0;
          TreeNode node = root;
      while (node.left != null) {
        depth++;
        node = node.left;
      }
      int last = calculationLast(0, depth, root);
      return (int) Math.pow(2, depth) - 1 + last;
    }

    public int calculationLast(int sum, int depth, TreeNode root) {
	if (depth != 1) {
	  TreeNode node = root.right;
	  for (int i = depth - 1; i > 0; i--)
	    node = node.left;
	  if (node == null) return calculationLast(sum, --depth, root.left);
	  else {
	    int dep = depth - 1;
	    return calculationLast(sum + (int) Math.pow(2, dep), dep, root.right);
	  }
	}
	if (root.right == null) return sum + 1;
	else return sum + 2;
     }
}
```

> 复杂度分析

进行logn次判断，每次判断不断变小，最后次数为1，所以均摊为d / 2，d是深度，总时间为logn * d / 2，时间复杂度O(logn * logn)

额外使用sum和一个指针变量协助判断，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Count Complete Tree Nodes.

Memory Usage: 41.6 MB, less than 9.76% of Java online submissions for Count Complete Tree Nodes.
