### LeetCode-547-number-of-provinces

> 题目链接

[LeetCode-547-number-of-provinces](https://leetcode-cn.com/problems/number-of-provinces/)

> 思路

深度检索，通过数组记录元素是否被检索过，防止无限循环

> 代码

```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        int n = isConnected.length;
        boolean[] visited = new boolean[n];
        int circles = 0;
        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                dfs(isConnected, visited, n, i);
                circles++;
            }
        }
        return circles;
    }

    public void dfs(int[][] isConnected, boolean[] visited, int n, int i) {
        for (int j = 0; j < n; j++) {
            if (isConnected[i][j] == 1 && !visited[j]) {
                visited[j] = true;
                dfs(isConnected, visited, n, j);
            }
        }
    }
}
```

> 复杂度分析

遍历二维数组的每一个位置，每个位置只会被检索一次，时间复杂度O(n ^ 2)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了95.44%的用户

内存消耗：39.3 MB, 在所有 Java 提交中击败了60.52%的用户
