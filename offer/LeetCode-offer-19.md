### LeetCode-offer-19

> 题目链接

[LeetCode-offer-19](https://leetcode-cn.com/problems/zheng-ze-biao-da-shi-pi-pei-lcof/)

> 思路

有*号时候，公式为f[i][j] = f[i - 1][j - 1]，否则f[i][j] = f[i][j - 2] || f[i - 1][j]，使用动态规划

> 代码

```java
class Solution {
    public boolean isMatch(String A, String B) {
        int n = A.length();
        int m = B.length();
        boolean[][] f = new boolean[n + 1][m + 1];
        for (int i = 0; i <= n; i++) {
            for (int j = 0; j <= m; j++) {
                if (j == 0) {
                    f[i][j] = i == 0;
                } else {
                    if (B.charAt(j - 1) != '*') {
                        if (i > 0 && (A.charAt(i - 1) == B.charAt(j - 1) || B.charAt(j - 1) == '.')) {
                            f[i][j] = f[i - 1][j - 1];
                        }
                    } else {
                        if (j >= 2) {
                            f[i][j] |= f[i][j - 2];
                        }
                        if (i >= 1 && j >= 2 && (A.charAt(i - 1) == B.charAt(j - 2) || B.charAt(j - 2) == '.')) {
                            f[i][j] |= f[i - 1][j];
                        }
                    }
                }
            }
        }
        return f[n][m];
    }
}
```

> 复杂度分析

遍历两个字符串，时间复杂度O(nm)

额外使用二维数组，空间复杂度O(nm)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.84%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了68.85%的用户
