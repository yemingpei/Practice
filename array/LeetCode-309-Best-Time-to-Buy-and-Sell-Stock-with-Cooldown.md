### LeetCode-309-Best-Time-to-Buy-and-Sell-Stock-with-Cooldown

> 题目链接

[LeetCode-309-Best-Time-to-Buy-and-Sell-Stock-with-Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

> 思路

分别处理i的三种情况，分别是持有股票，卖出股票（处于冷却期），卖出股票还没有买进

> 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        int held = Integer.MIN_VALUE;
        int sold = Integer.MIN_VALUE;
        int reset = 0;
        for (int i = 0; i < prices.length; i++) {
            int temp = sold;
            sold = held + prices[i];
            held = Math.max(held, reset - prices[i]);
            reset = Math.max(reset, temp);
        }
        return Math.max(reset, sold);
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

临时保存了三个状态量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Best Time to Buy and Sell Stock with Cooldown.

Memory Usage: 36.9 MB, less than 69.25% of Java online submissions for Best Time to Buy and Sell Stock with Cooldown.
