### LeetCode-10-Regular-Expression-Matching

> 题目链接

[LeetCode-10-Regular-Expression-Matching](https://leetcode.com/problems/regular-expression-matching/)

> 思路

用boolean[text.length() + 1][pattern.length() + 1]来记录子结构是否match，自底向上，'*'要特别比较pattern后第二位，或者text后一位是否match，
其他情况取决于后一个比较是否match

> 代码

```java
class Solution {
    public boolean isMatch(String text, String pattern) {
        boolean[][] dp = new boolean[text.length() + 1][pattern.length() + 1];
        dp[text.length()][pattern.length()] = true;
        for (int i = text.length(); i >= 0; i--){
            for (int j = pattern.length() - 1; j >= 0; j--){
                boolean first_match = (i < text.length() && (pattern.charAt(j) == text.charAt(i) || pattern.charAt(j) == '.'));
                if (j + 1 < pattern.length() && pattern.charAt(j+1) == '*'){
                    dp[i][j] = dp[i][j+2] || first_match && dp[i+1][j];
                } else {
                    dp[i][j] = first_match && dp[i+1][j+1];
                }
            }
        }
        return dp[0][0];
    }
}
```

> 复杂度分析

双循环遍历对应的text和pattern，时间复杂度O(n ^ 2)

额外使用boolean的二维数组来辅助，空间复杂度O(n ^ 2)

> 总结

Runtime: 5 ms, faster than 69.15% of Java online submissions for Regular Expression Matching.

Memory Usage: 39.8 MB, less than 27.39% of Java online submissions for Regular Expression Matching.
