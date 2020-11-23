### LeetCode-292-Nim-Game

> 题目链接

[LeetCode-292-Nim-Game](https://leetcode.com/problems/nim-game/)

> 思路

判断除以4，是否能整除，先手则先取余数个，然后别人取1，我取3，若别人取2，我取2，若别人取3，我取1，保持一回合双方下来，一共为4，所以木有余数的话，我就输了，否则，我赢

> 代码

```java
class Solution {
    public boolean canWinNim(int n) {
        return n % 4 != 0;
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Nim Game.

Memory Usage: 35.3 MB, less than 97.29% of Java online submissions for Nim Game.
