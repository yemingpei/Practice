### LeetCode-446-Arithmetic-Slices-II-Subsequence

> 题目链接

[LeetCode-446-Arithmetic-Slices-II-Subsequence](https://leetcode.com/problems/arithmetic-slices-ii-subsequence/)

> 思路

动态规划公式为f[i][A[i] - A[j]] += (f[j][A[i] - A[j]] + 1)

> 代码

```java
class Solution {
    public int numberOfArithmeticSlices(int[] A) {
        int n = A.length;
        HashMap<Integer, LinkedList<Integer>> locMap = new HashMap<>();
        for (int i = 0; i < n; i++) {
            LinkedList<Integer> loc = locMap.get(A[i]);
            if (loc == null) {
                loc = new LinkedList<>();
                locMap.put(A[i], loc);
            }
            loc.add(i);
        }
        int ans = 0;
        int[][] dp = new int[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                long prev = 2l * A[j] - A[i];
                if (prev < Integer.MIN_VALUE || prev > Integer.MAX_VALUE) {
                    continue;
                }
                LinkedList<Integer> loc = locMap.get((int) prev);
                if (loc != null) {
                    for (int k: loc) {
                        if (k >= j) {
                            break;
                        }
                        dp[i][j] += dp[j][k] + 1;
                    }
                    ans += dp[i][j];
                }
            }
        }
        return ans;
    }
}
```

> 复杂度分析

双重循环，时间复杂度O(n ^ 2)

额外二维数组保存数据，空间复杂度O(n ^ 2)

> 总结

Runtime: 68 ms, faster than 92.67% of Java online submissions for Arithmetic Slices II - Subsequence.

Memory Usage: 58.9 MB, less than 90.09% of Java online submissions for Arithmetic Slices II - Subsequence.
