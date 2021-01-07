### LeetCode-375-Guess-Number-Higher-or-Lower-II

> 题目链接

[LeetCode-375-Guess-Number-Higher-or-Lower-II](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)

> 思路

拆分子问题，mid添加前半部分的最小值和后半部分的最小值，综合得出当前需要的最小值，因为右边肯定大于左边，所以不断挑战右边的区域，需要最大值就可以

> 代码

```java
class Solution {
    int[][] dp;
    public int getMoneyAmount(int n) {
        dp = new int[n + 1][n + 1];
        return getMoneyAmount(1, n);
    }
    private int getMoneyAmount(int start, int end) {
        if (dp[start][end] != 0) return dp[start][end];
        if (start >= end) return 0;
        if (start >= end - 2) return dp[start][end] = end - 1;
        int mid = (start + end) / 2 - 1, min = Integer.MAX_VALUE;
        while (mid < end) {
            int left = getMoneyAmount(start, mid - 1), right = getMoneyAmount(mid + 1, end);
            min = Math.min(min, mid + Math.max(left, right));
            if (right <= left) break;
            mid++;
        }
        return dp[start][end] = min;
    }
}
```

> 复杂度分析

二进制实现快速查询，时间复杂度O(n ^ 2 * logn)

额外使用boolean的二维数组来辅助，空间复杂度O(n ^ 2)

> 总结

Runtime: 3 ms, faster than 99.43% of Java online submissions for Guess Number Higher or Lower II.

Memory Usage: 37.8 MB, less than 92.47% of Java online submissions for Guess Number Higher or Lower II.
