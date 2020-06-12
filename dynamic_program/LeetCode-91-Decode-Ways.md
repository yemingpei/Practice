### LeetCode-91-Decode-Ways

> 题目链接

[LeetCode-91-Decode-Ways](https://leetcode.com/problems/decode-ways/)

> 思路

迭代公式count[n] = count[n - 1] + count[n - 2],如果位置为0，则跳过，双数字大于26也跳过

> 代码

```java
class Solution {
    public int numDecodings(String s) {
        if(s == null || s.length() == 0) return 0;
        int[] dp = new int[s.length()+1];
        dp[0] = 1;
        dp[1] = s.charAt(0) == '0'? 0:1;
        for(int i = 2; i <=s.length(); i++) {
            if(s.charAt(i-1) != '0') {
                dp[i] = dp[i-1];
            }
            int twoDigit = (s.charAt(i-2) - '0') * 10 + (s.charAt(i-1) - '0');
            if(twoDigit >= 10 && twoDigit <= 26) {
                dp[i] += dp[i-2];
            }
        }
        return dp[dp.length-1];
    }
}
```

> 复杂度分析

遍历整个string，时间复杂度O(n)

用int数组来记录count，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 97.63% of Java online submissions for Decode Ways.

Memory Usage: 37.5 MB, less than 94.46% of Java online submissions for Decode Ways.
