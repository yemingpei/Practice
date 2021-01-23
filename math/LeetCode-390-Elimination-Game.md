### LeetCode-390-Elimination-Game

> 题目链接

[LeetCode-390-Elimination-Game](https://leetcode.com/problems/elimination-game/)

> 思路

```java
原数组     1 2 3 4 5 6 7 8 9
第一轮剔除 2 4 6 8
集体除以2  1 2 3 4
第二次剔除 2 6
集体除以2  1 3
第三次剔除 6
          1
```
由此可见 f(n) = 2 * (n / 2 + 1 - f(n/2)

> 代码

```java
class Solution {
    public int lastRemaining(int n) {
        return n == 1 ? 1 : 2 * (n / 2 + 1 - lastRemaining(n / 2));
    }
}
```

> 复杂度分析

不断除2递归，时间复杂度O(logn)

递归层数，空间复杂度O(logn)

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Elimination Game.

Memory Usage: 37.9 MB, less than 78.40% of Java online submissions for Elimination Game.
