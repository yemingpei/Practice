### LeetCode-145-Binary-Tree-Postorder-Traversal

> 题目链接

[LeetCode-145-Binary-Tree-Postorder-Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

> 思路

利用栈胡或者队列保存节点，辅助完成后序遍历，模拟后序遍历

> 代码

```java
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
         List<Integer> result = new ArrayList<Integer>();
	       if (root == null) return result;
		     Deque<TreeNode> stack = new LinkedList<TreeNode>();
		     TreeNode node = root, before = null, top = null;
		     while (node != null || !stack.isEmpty()) {
			       if (node != null) {
				     stack.push(node);
				     node = node.left;
			       } else {
				          top = stack.peek();
				          if (top.right != null && !top.right.equals(before)) node = top.right;
                  else {
					            stack.pop();
					            result.add(top.val);
					            before = top;
				          }
			      }
		    }
		    return result;
    }
}
```

> 复杂度分析

遍历整棵树，时间复杂度O(n)

额外使用了队列来辅助完成，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Binary Tree Postorder Traversal.

Memory Usage: 37.8 MB, less than 46.08% of Java online submissions for Binary Tree Postorder Traversal.
