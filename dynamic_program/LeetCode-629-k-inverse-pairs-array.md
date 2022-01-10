### LeetCode-629-k-inverse-pairs-array

> 题目链接

[LeetCode-629-k-inverse-pairs-array](https://leetcode-cn.com/problems/k-inverse-pairs-array/)

> 思路

动态规划公式：dp[i][j] = dp[i - 1][j] - dp[i - 1][j - i]

> 代码

```java
class Solution {
    public int kInversePairs(int n, int k) {
        int[][] dp = new int[n + 1][k + 1];
        for (int i = 0; i <= n; i++) {
            dp[i][0] = 1; 
        }
        int mod = (int)1e9 + 7;
        for (int i = 1; i <= n; i++) {
            long temp = dp[i - 1][0];
            for (int j = 1; j <= k; j++) {
                temp += dp[i - 1][j];
                if (j >= i) {
                    temp -= dp[i - 1][j - i];
                }
                dp[i][j] = (int)(temp % mod); 
            }
        }
        return dp[n][k];
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(nk)

额外使用数组，空间复杂度O(nk)

> 总结

执行用时：10 ms, 在所有 Java 提交中击败了99.76%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了40.68%的用户
