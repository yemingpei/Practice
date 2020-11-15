### LeetCode-312-Burst-Balloons

> 题目链接

[LeetCode-312-Burst-Balloons](https://leetcode.com/problems/burst-balloons/)

> 思路

dp[i][j]表示i到j的最大收益，则有动态规划公式 dp[i][j] = max(dp[i][j], nums[i - 1]*nums[k]*nums[j + 1] + dp[i][k - 1] + dp[k + 1][j]) 

> 代码

```java
class Solution {
    public int maxCoins(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int len = nums.length;
        int newLen = len + 2;
        int[] newNums = new int[newLen];
        for (int i = 1; i <= len; i++) {
            newNums[i] = nums[i - 1];
        }
        newNums[0] = 1;
        newNums[newLen - 1] = 1;
        int[][] dp = new int[newLen][newLen];
        for (int gap = 2; gap < newLen; gap++) {
            for (int left = 0; left < newLen - gap; left++) {
                int curr = 0;
                int right = left + gap;
                for (int i = left + 1; i < right; i++) {
                    curr = Math.max(curr, dp[left][i] + dp[i][right] + newNums[left] * newNums[i] * newNums[right]);
                }
                dp[left][right] = curr;
            }
        }
        return dp[0][newLen - 1];
    }
}
```

> 复杂度分析

三重循环，时间复杂度O(n ^ 3)

额外使用二维数组来辅助，空间复杂度O(n ^ 2)

> 总结

Runtime: 5 ms, faster than 99.01% of Java online submissions for Burst Balloons.

Memory Usage: 36.8 MB, less than 39.95% of Java online submissions for Burst Balloons.
