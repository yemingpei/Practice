### LeetCode-188-Best-Time-to-Buy-and-Sell-Stock-IV

> 题目链接

[LeetCode-188-Best-Time-to-Buy-and-Sell-Stock-IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)

> 思路

2 * k > n时候，取可能的最大值，否则，利用最小负值来累积前一笔交易的数量

> 代码

```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        int n = prices.length;
        if (n <= 0 || k <= 0) return 0;
        if (2 * k > n) {
            int profit = 0;
            for (int i = 1; i < n; i++) {
                profit += Math.max(0, prices[i] - prices[i - 1]);
            }
            return profit;
        }
        int[] profit = new int[k + 1];
        int[] lowprices = new int[k + 1];
        for (int i = 0; i < lowprices.length; i++) 
                lowprices[i] = Integer.MAX_VALUE;
        for (int p : prices) {
            for (int i = k; i > 0; i--) {
              profit[i] = Math.max(profit[i], p - lowprices[i]);
              lowprices[i] = Math.min(lowprices[i], p - profit[i - 1]);
            } 
        }
        return profit[k];
    }

}
```

> 复杂度分析

最多遍历n * n / 2次，时间复杂度O(n ^ 2)

k的最大值为n / 2，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.84% of Java online submissions for Best Time to Buy and Sell Stock IV.

Memory Usage: 39.6 MB, less than 65.98% of Java online submissions for Best Time to Buy and Sell Stock IV.
