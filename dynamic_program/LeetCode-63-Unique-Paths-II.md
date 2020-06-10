### LeetCode-63-Unique-Paths-II

> 题目链接

[LeetCode-63-Unique-Paths-II](https://leetcode.com/problems/unique-paths-ii/)

> 思路

迭代公式count[m][n] = count[m - 1][n] + count[m][n - 1],推导最后格子的次数和LeetCode-62-Unique-Paths区别在于数组初始化操作

> 代码

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int row = obstacleGrid.length;
        int column = obstacleGrid[0].length;
        obstacleGrid[0][0] = obstacleGrid[0][0] == 1? 0 : 1;
        for(int i = 1; i < column; i++)
            obstacleGrid[0][i] = obstacleGrid[0][i] == 1? 0 : obstacleGrid[0][i -1];
        for(int j = 1; j < row; j++)
            obstacleGrid[j][0] = obstacleGrid[j][0] == 1? 0 : obstacleGrid[j - 1][0];
        for(int j = 1; j < row; j++)
            for(int i = 1; i < column; i++)
                obstacleGrid[j][i] = obstacleGrid[j][i] == 1? 0 : obstacleGrid[j-1][i] + obstacleGrid[j][i-1];
        return obstacleGrid[row-1][column-1];
    }
}
```

> 复杂度分析

遍历整个数组，时间复杂度O(n * m)

在原数组上记录count，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Unique Paths II.

Memory Usage: 37.4 MB, less than 95.39% of Java online submissions for Unique Paths II.
