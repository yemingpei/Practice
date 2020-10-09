### LeetCode-221-Maximal-Square

> 题目链接

[LeetCode-221-Maximal-Square](https://leetcode.com/problems/maximal-square/)

> 思路

动态规划公式dp[i][j] = Math.min(Math.min(dp[i-1][j], dp[i][j-1]),dp[i-1][j-1]) + 1 , 二维数组的动态规划

> 代码

```java
class Solution {
    public int maximalSquare(char[][] matrix) {
        int result = 0;
        int row = matrix.length;
        if(row == 0) return result;
        int column = matrix[0].length;
        if(column == 0)return result;
        int[][] dp = new int[row][column];
        for(int i = 0; i < row; i++)
            for(int j = 0; j < column; j++){
                if(matrix[i][j] == '1'){
                    if(i == 0 || j ==0)
                        dp[i][j] = 1;
                    else{
                        dp[i][j] = Math.min(Math.min(dp[i-1][j], dp[i][j-1]),dp[i-1][j-1]) + 1;
                    }
                    result = Math.max(result, dp[i][j]);
                }
            }
        return result * result;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(m * n)

额外使用二维数组记录(i，j)的最大边长，空间复杂度O(m * n)

> 总结

Runtime: 4 ms, faster than 88.05% of Java online submissions for Maximal Square.

Memory Usage: 42 MB, less than 8.04% of Java online submissions for Maximal Square.
