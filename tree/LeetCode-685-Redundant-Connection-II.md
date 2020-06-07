### LeetCode-685-Redundant-Connection-II

> 题目链接

[LeetCode-685-Redundant-Connection-II](https://leetcode.com/problems/redundant-connection-ii/)

> 思路

首先寻找是否有两个父亲的节点，然后寻找成为环的点，然后剔除，使用暴力法

> 代码

```java
class Solution {
    public int[] findRedundantDirectedConnection(int[][] edges) {
		int n = edges.length;
		int[] twoParent = null;
		int[] ring = null;
		int[] parent = new int[n + 1];
		for (int i = 0; i <= n; i++)
			parent[i] = i;
		for (int i = 0; i < edges.length; i++) {
			int left = find(parent, edges[i][0]);
			int right = find(parent, edges[i][1]);
			if (right != edges[i][1]) twoParent = edges[i];
			else if (left == right) ring = edges[i];
			else parent[right] = left;
		}
		if (twoParent == null) return ring;
		if (ring == null) return twoParent;
		for (int[] edge : edges)
			if (edge[1] == twoParent[1])
				return edge;
		return twoParent;
	}

	private int find(int[] parents, int val) {
		while (val != parents[val]) {
			parents[val] = parents[parents[val]];
			val = parents[val];
		}
		return val;
	}
}
```

> 复杂度分析

反复寻找多个树的关系，时间复杂度O(n ^ 2)

额外使用了int数组来构建父子关系，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 94.67% of Java online submissions for Redundant Connection II.

Memory Usage: 39.6 MB, less than 62.23% of Java online submissions for Redundant Connection II.
