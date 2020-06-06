### LeetCode-297-Serialize-and-Deserialize-Binary-Tree

> 题目链接

[LeetCode-297-Serialize-and-Deserialize-Binary-Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

> 思路

遍历一遍树，拼接成数组；遍历String数组，利用队列还原树

> 代码

```java
public class Codec {
	public String serialize(TreeNode root) {
		StringBuilder sb = new StringBuilder();
		serializeHelper(root, sb);
		return sb.toString();
	}

	private void serializeHelper(TreeNode root, StringBuilder sb) {
		if (root == null) {
			sb.append(',');
			return;
		}
		sb.append(root.val).append(',');
		serializeHelper(root.left, sb);
		serializeHelper(root.right, sb);
	}

	public TreeNode deserialize(String data) {
		Queue<String> q = new LinkedList<>();
		String[] tokens = data.split(",");
		for (String str : tokens) q.offer(str);
		return deserializeHelper(q);
	}

	private TreeNode deserializeHelper(Queue<String> q) {
		if (q.isEmpty()) return null;
		String str = q.poll();
		if (str.equals("")) return null;
		TreeNode node = new TreeNode(Integer.parseInt(str));
		node.left = deserializeHelper(q);
		node.right = deserializeHelper(q);
		return node;
	}
}
```

> 复杂度分析

遍历了树，以及遍历了String数组，时间复杂度O(n)

利用了队列来辅助，空间复杂度O(n)

> 总结

Runtime: 6 ms, faster than 90.78% of Java online submissions for Serialize and Deserialize Binary Tree.

Memory Usage: 49 MB, less than 12.58% of Java online submissions for Serialize and Deserialize Binary Tree.
