### LeetCode-132-Palindrome-Partitioning-II

> 题目链接

[LeetCode-132-Palindrome-Partitioning-II](https://leetcode.com/problems/palindrome-partitioning-ii/)

> 思路

动态规划公式  dp[j] = Math.min(dp[j], (i == 0 ? 0 : dp[i - 1] + 1))

> 代码

```java
class Solution {
    public int minCut(String s){
        int[] dp = new int[s.length()];
        Arrays.fill(dp, s.length() - 1);
        char[] chars = s.toCharArray();
        for(int i = 0; i < chars.length; i++){
            isPalindrome(chars, i, i, dp);
            isPalindrome(chars, i, i + 1, dp);
        }
        return dp[s.length() - 1];
    }
    private void isPalindrome(char[] chars, int i, int j, int[] dp){
        int len = chars.length;
        while(i >= 0 && j < len && chars[i] == chars[j]){
            dp[j] = Math.min(dp[j], (i == 0 ? 0 : dp[i - 1] + 1));
            i--;
            j++;
        }
    }
}
```

> 复杂度分析

比较二维坐标，时间复杂度O(n ^ 2)

用int数组来记录分割次数t，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.60% of Java online submissions for Palindrome Partitioning II.

Memory Usage: 37.4 MB, less than 92.94% of Java online submissions for Palindrome Partitioning II.
