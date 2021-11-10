### LeetCode-518-coin-change-2

> 题目链接

[LeetCode-518-coin-change-2](https://leetcode-cn.com/problems/coin-change-2/)

> 思路

动态规划公式dp[i] += dp[i - coin]

> 代码

```java
class Solution {
    public int change(int amount, int[] coins) {
        int[] dp = new int[amount + 1];
        dp[0] = 1;
        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }
        return dp[amount];
    }
}
```

> 复杂度分析

遍历双重数组，时间复杂度O(amount * n)

额外使用数组，空间复杂度O(amount)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.1 MB, 在所有 Java 提交中击败了24.64%的用户
