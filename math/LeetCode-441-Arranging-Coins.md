### LeetCode-441-Arranging-Coins

> 题目链接

[LeetCode-441-Arranging-Coins](https://leetcode.com/problems/arranging-coins/)

> 思路

k*(k + 1)/2 <= n,需要找到最大的k值

> 代码

```java
class Solution {
    public int arrangeCoins(int n) {
        return (int)(Math.sqrt(2) * Math.sqrt(n + 0.125) - 0.5);
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

无额外使用变量值，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Arranging Coins.

Memory Usage: 36.1 MB, less than 78.23% of Java online submissions for Arranging Coins.
