### LeetCode-123-Best-Time-to-Buy-and-Sell-Stock-III

> 题目链接

[LeetCode-123-Best-Time-to-Buy-and-Sell-Stock-III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

> 思路

```java
//例如[1,2,4,2,5,7,2,4,9,0]，买入点为1，第一卖出点是7，第二买入点是2，第二卖出点是9
```

先寻找最低价作为买点，再比较最佳卖点，再通过负数得出第二买点，记录收益，通过第二卖点得出两笔交易的最大收益

> 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        int low1 = Integer.MAX_VALUE;
        int low2 = Integer.MAX_VALUE;
        int gap1 = 0;
        int gap2 = 0;
        for (int price : prices) {
            low1 = Math.min(low1, price);
            gap1 = Math.max(gap1, price - low1);
            low2 = Math.min(low2, price - gap1);
            gap2 = Math.max(gap2, price - low2);
        }
        return gap2;
    }
}
```

> 复杂度分析

遍历一遍价格，时间复杂度O(n)

额外四个变量保存结果，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 92.42% of Java online submissions for Best Time to Buy and Sell Stock III.

Memory Usage: 39.7 MB, less than 10.81% of Java online submissions for Best Time to Buy and Sell Stock III.
