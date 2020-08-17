### LeetCode-122-Best-Time-to-Buy-and-Sell-Stock-II

> 题目链接

[LeetCode-122-Best-Time-to-Buy-and-Sell-Stock-II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

> 思路

先看例子

```java
//例子：[7,1,5,3,6,4]
```
1的时候买入，5的时候卖出，3的时候买入，6的时候卖出，无限波段，寻找不断往上升的趋势为收入

> 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        int amount = 0;
        for(int i = 1; i < prices.length; i++){
            if(prices[i] > prices[i - 1])
                amount = amount + (prices[i] - prices[i - 1]);
        }
        return amount;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度应该为O(n)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 94.50% of Java online submissions for Best Time to Buy and Sell Stock II.

Memory Usage: 39.2 MB, less than 87.44% of Java online submissions for Best Time to Buy and Sell Stock II.
