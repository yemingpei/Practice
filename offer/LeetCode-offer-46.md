### LeetCode-offer-46

> 题目链接

[LeetCode-offer-46](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

> 思路

如果最近两位可以翻译成功，f(n) = f(n -1) + f(n - 2)，否则 f(n) = f(n -1)

> 代码

```java
class Solution {
    public int translateNum(int num) {
        char[] c = String.valueOf(num).toCharArray();
        int len = c.length;
        int[] dp = new int[len + 1];
        dp[0] = 1;
        dp[1] = 1;
        for(int i = 2; i < len + 1; i++){
            int sum = (c[i - 2] - '0') * 10 + (c[i-1] - '0');
            if(sum >= 10 && sum <= 25) dp[i] = dp[i - 1] + dp[i - 2];
            else dp[i] = dp[i - 1];
        }
        return dp[len];
    }
}
```

> 复杂度分析

动态规划，时间复杂度O(n)

额外使用字符数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.5 MB, 在所有 Java 提交中击败了11.21%的用户
