### LeetCode-458-Poor-Pigs

> 题目链接

[LeetCode-458-Poor-Pigs](https://leetcode.com/problems/poor-pigs/)

> 思路

x ≥ log(buckets) / log(states)

> 代码

```java
class Solution {
    public int poorPigs(int buckets, int minutesToDie, int minutesToTest) {
        int states = minutesToTest / minutesToDie + 1;
        return (int) Math.ceil(Math.log(buckets) / Math.log(states));
    }
}
```

> 复杂度分析

公式法计算，时间复杂度O(1)

额外使用一个常数类型，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Poor Pigs.

Memory Usage: 35.9 MB, less than 41.46% of Java online submissions for Poor Pigs.
