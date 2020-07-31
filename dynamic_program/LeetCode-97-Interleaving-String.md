### LeetCode-97-Interleaving-String

> 题目链接

[LeetCode-97-Interleaving-String](https://leetcode.com/problems/interleaving-string/)

> 思路

例子 s1 = "ac", s2 = "ab", s3 = "aabc" 
|   | 0 | a | b |
| 0 | 1 | 1 | 0 |
| a | 1 | 1 | 1 |
| c | 0 | 0 | 1 |

如上所示，从起点(0,0)开始走（只能选择向下或者向右），往下为选择S1，往右为选择S2，能走到终点(n,m)，就是输出true，否则false。

> 代码

```java
class Solution {
    public boolean isInterleave(String s1, String s2, String s3) {
        int n = s1.length();
        int m = s2.length();
        int length = s3.length();
        if(n + m != length) return false;
        boolean[][] path = new boolean[n + 1][m + 1];
        path[0][0] = true;
        for(int i = 1; i <= n; i++)
            path[i][0] = path[i - 1][0] && s3.charAt(i - 1) == s1.charAt(i - 1);
        for(int j = 1; j <= m; j++)
            path[0][j] = path[0][j - 1] && s3.charAt(j - 1) == s2.charAt(j - 1);
        for(int i = 1; i <= n; i++)
            for(int j = 1; j <= m; j++)
                path[i][j] = (path[i - 1][j] && s1.charAt(i - 1) == s3.charAt(i + j - 1)) || (path[i][j - 1] && s2.charAt(j-1) == s3.charAt(i + j - 1));
        return path[n][m];
    }
}
```

> 复杂度分析

遍历走完二维数组，时间复杂度O(m * n)

额外使用二维数组保存结果，空间复杂度O(m * n)

> 总结

Runtime: 2 ms, faster than 84.96% of Java online submissions for Interleaving String.

Memory Usage: 38.1 MB, less than 20.00% of Java online submissions for Interleaving String.
