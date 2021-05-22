### LeetCode-offer-63

> 题目链接

[LeetCode-offer-63](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

> 思路

记录最小值，然后每次计算，保存最大的差值

> 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length < 2) return 0;
        int min = prices[0];
        int win = 0;
        for(int i = 1; i < prices.length; i++){
            win = Math.max(win, prices[i] - min);
            min = Math.min(min, prices[i]);
        }
        return win;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n)

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了66.46%的用户

内存消耗：38.5 MB, 在所有 Java 提交中击败了20.37%的用户
