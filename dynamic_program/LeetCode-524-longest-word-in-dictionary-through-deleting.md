### LeetCode-524-longest-word-in-dictionary-through-deleting

> 题目链接

[LeetCode-524-longest-word-in-dictionary-through-deleting](https://leetcode-cn.com/problems/longest-word-in-dictionary-through-deleting/)

> 思路

动态规划，用转换公式，快速把s的字符信息保存，dp[i][j] = dp[i + 1][j]

> 代码

```java
class Solution {
    public String findLongestWord(String s, List<String> dictionary) {
        int n = s.length();
        int size = 26;
        int[][] dp = new int[n + 1][26];
        Arrays.fill(dp[n], n);
        for (int i = n - 1; i >= 0; i--) {
            int c = s.charAt(i) - 'a';
            for (int j = 0; j < size; j++) {
                dp[i][j] = dp[i + 1][j];
            }
            dp[i][c] = i;
        }
        String result = "";
        for (String str : dictionary) {
            int len1 = str.length();
            int len2 = result.length();
            if (len1 >= len2 && valid(dp, str)) {
                if (len1 > len2 || str.compareTo(result) < 0) {
                    result = str;
                }
            }
        }
        return result;
    }

    private boolean valid(int[][] dp, String str) {
        int n = dp.length - 1;
        int m = str.length();
        for (int i = 0, j = 0; i < m; i++) {
            int idx = str.charAt(i) - 'a';
            j = dp[j][idx];
            if (j == n) {
                return false;
            } else {
                j++;
            }
        }
        return true;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了99.98%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了95.77%的用户
