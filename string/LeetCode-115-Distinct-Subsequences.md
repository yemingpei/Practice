### LeetCode-115-Distinct-Subsequences

> 题目链接

[LeetCode-115-Distinct-Subsequences](https://leetcode.com/problems/distinct-subsequences/)

> 思路

暴力法，循环遍历两个字符串，待匹配字符串倒序遍历

> 代码

```java
class Solution {
    public int numDistinct(String s, String t) {
        int[] dp = new int[t.length() + 1];
        dp[0] = 1;
        for (int i = 0; i < s.length(); i++){
            for (int j = t.length() - 1; j >= 0; j--) {
                if (t.charAt(j) == s.charAt(i)) {
                    dp[j + 1] += dp[j];
                }
            }
        }
        return dp[t.length()];
    }
}
```

> 复杂度分析

循环遍历两个字符串，时间复杂度O(m * n)

额外使用数组保存结果，空间复杂度O(m)

> 总结

Runtime: 3 ms, faster than 98.91% of Java online submissions for Distinct Subsequences.

Memory Usage: 37.6 MB, less than 89.01% of Java online submissions for Distinct Subsequences.
