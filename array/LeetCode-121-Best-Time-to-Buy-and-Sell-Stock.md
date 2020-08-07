### LeetCode-121-Best-Time-to-Buy-and-Sell-Stock

> 题目链接

[LeetCode-121-Best-Time-to-Buy-and-Sell-Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

> 思路

保存最小值，通过当前价格和最小值的差，来得出当天卖出的最大收益

> 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length == 0) return 0;
        int gain = 0;
        int min = prices[0];
        for(int i = 1; i < prices.length; i++){
            gain = Math.max(gain, prices[i] - min);
            min = Math.min(min, prices[i]);
        }
        return gain;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要两个常量int来记录最小值和最大收益，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.42% of Java online submissions for Best Time to Buy and Sell Stock.

Memory Usage: 39.9 MB, less than 5.25% of Java online submissions for Best Time to Buy and Sell Stock.
