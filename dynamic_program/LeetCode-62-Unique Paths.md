### LeetCode-62-Unique Paths

> 题目链接

[LeetCode-62-Unique Paths](https://leetcode.com/problems/unique-paths/)

> 思路

迭代公式count[m][n] = count[m - 1][n] + count[m][n - 1],推导最后格子的次数

> 代码

```java
class Solution {
    public int uniquePaths(int m, int n) {
		int[][] count = new int[n][m];
		for (int i = 0; i < m; i++)
			count[0][i] = 1;
		for (int j = 0; j < n; j++)
			count[j][0] = 1;
		for (int j = 1; j < n; j++)
			for (int i = 1; i < m; i++)
				count[j][i] = count[j - 1][i] + count[j][i - 1];
		return count[n - 1][m - 1];
	}
}
```

> 复杂度分析

遍历真个数组，时间复杂度O(n * m)

额外使用空间保存每个格子的次数，空间复杂度O(n * m)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Unique Paths.

Memory Usage: 36.2 MB, less than 61.71% of Java online submissions for Unique Paths.
