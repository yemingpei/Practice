### LeetCode-face-17-24

> 题目链接

[LeetCode-face-17-24](https://leetcode-cn.com/problems/max-submatrix-lcci/)

> 思路

计算矩阵的大小，通过计算图形的面积的相关公式完成，先计算前缀和，减少计算量

> 代码

```java
class Solution {
    public int[] getMaxMatrix(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        int[][] dp = new int[m + 1][n];
        for(int j = 0; j < n; j ++) {
            for(int i = 1; i <= m; i ++)
                dp[i][j] = dp[i - 1][j] + matrix[i - 1][j];
        }
        int[] ans = new int[4];
        int maxSum = matrix[0][0];
        for(int i = 1; i <= m; i ++) {
            for(int j = i - 1; j >= 0; j --) {
                int sum = dp[i][0] - dp[j][0], begin = 0;
                for(int k = 1; k < n; k ++) {
                    if(sum > 0) sum += dp[i][k] - dp[j][k];
                    else {
                        sum = dp[i][k] - dp[j][k];
                        begin = k;
                    }
                    if(sum > maxSum) {
                        ans[0] = j;
                        ans[1] = begin;
                        ans[2] = i - 1;
                        ans[3] = k;
                        maxSum = sum;
                    }
                }
            }
        }
        return ans;
    }
}
```

> 复杂度分析

三重循环，时间复杂度O(n ^ 3)

额外使用二维数组，空间复杂度O(n ^ 2)

> 总结

执行用时：39 ms, 在所有 Java 提交中击败了99.81%的用户

内存消耗：42.5 MB, 在所有 Java 提交中击败了76.21%的用户
