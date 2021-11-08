### LeetCode-516-longest-palindromic-subsequence

> 题目链接

[LeetCode-516-longest-palindromic-subsequence](https://leetcode-cn.com/problems/longest-palindromic-subsequence/)

> 思路

动态规划，公式 dp[i][j] = dp[i + 1][j - 1] + 2 or dp[i][j] = Math.max(dp[i + 1][j], dp[i][j - 1])

> 代码

```java
class Solution {
    public int longestPalindromeSubseq(String s) {
        int n = s.length();
        int[][] dp = new int[n][n];
        for (int i = n - 1; i >= 0; i--) {
            dp[i][i] = 1;
            char c1 = s.charAt(i);
            for (int j = i + 1; j < n; j++) {
                char c2 = s.charAt(j);
                if (c1 == c2) {
                    dp[i][j] = dp[i + 1][j - 1] + 2;
                } else {
                    dp[i][j] = Math.max(dp[i + 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[0][n - 1];
    }
}
```

> 复杂度分析

二维遍历数组，时间复杂度O(n ^ 2)

额外使用二维数组，空间复杂度O(n ^ 2)

> 总结

执行用时：25 ms, 在所有 Java 提交中击败了89.77%的用户

内存消耗：48.3 MB, 在所有 Java 提交中击败了51.63%的用户
