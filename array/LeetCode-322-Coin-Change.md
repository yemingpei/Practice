### LeetCode-322-Coin-Change

> 题目链接

[LeetCode-322-Coin-Change](https://leetcode.com/problems/coin-change/)

> 思路

贪心算法，要个数少，那么硬币需要尽可能大，所以如果大的硬币能整除，那能最快得出答案，否则就要分拆这个大的硬币。再利用局部贪心

> 代码

```java
class Solution {
    private int result = Integer.MAX_VALUE;
    
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) return 0;
        if (coins.length == 0) return -1;
        Arrays.sort(coins);
        if (amount < coins[0]) return -1;
        dfs(coins, coins.length - 1, amount, 0);
        return (result == Integer.MAX_VALUE) ? -1 : result;
    }
    
    private void dfs(int[] coins, int index, int amount, int curr) {
        if (index < 0) return;
        int val = amount % coins[index];
        int count = amount / coins[index];
        if (val == 0) {
            result = Math.min(result, curr + count);
            return;
        }
        for (int i = count; i >= 0; i--) {
            if (curr + i >= result - 1) break;
            dfs(coins, index - 1, amount - i * coins[index], curr + i);
        }
    }
}
```

> 复杂度分析

排序，时间复杂度O(nlogn)

递归栈，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Coin Change.

Memory Usage: 36.8 MB, less than 99.01% of Java online submissions for Coin Change.
