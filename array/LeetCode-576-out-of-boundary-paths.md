### LeetCode-576-out-of-boundary-paths

> 题目链接

[LeetCode-576-out-of-boundary-paths](https://leetcode-cn.com/problems/out-of-boundary-paths/)

> 思路

利用记忆法记录已经检索过的数据，避免重复计算

> 代码

```java
class Solution {
    int MOD = 1000000007;
    public int findPaths(int m, int n, int maxMove, int startRow, int startColumn) {
        int[][][] result = new int[m][n][maxMove + 1];
        for(int i = 0; i < m; i++)
            for(int j = 0; j < n; j++)
                for(int z = 1; z <= maxMove ; z++){
                    result[i][j][z] = -1;
                }
        return getPaths(m, n, maxMove, startRow, startColumn, result);
    }
    public int getPaths(int m, int n, int maxMove, int startRow, int startColumn, int[][][] result) {
        if(startRow < 0 || startColumn < 0 || startRow == m || startColumn == n) return 1;
        if(maxMove == 0) return 0;
        if(result[startRow][startColumn][maxMove] != -1) return result[startRow][startColumn][maxMove];
        int sum = getPaths(m, n, maxMove - 1, startRow - 1, startColumn, result);
        sum = (sum + getPaths(m, n, maxMove - 1, startRow, startColumn - 1, result)) % MOD;
        sum = (sum + getPaths(m, n, maxMove - 1, startRow + 1, startColumn, result)) % MOD; 
        sum = (sum + getPaths(m, n, maxMove - 1, startRow, startColumn + 1, result)) % MOD;
        result[startRow][startColumn][maxMove] = sum;
        return sum;
    }
}
```

> 复杂度分析

遍历三维数组，时间复杂度O(mnmaxMove)

额外使用三维数组，空间复杂度O(mnmaxMove)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了99.18%的用户

内存消耗：37.6 MB, 在所有 Java 提交中击败了61.68%的用户
