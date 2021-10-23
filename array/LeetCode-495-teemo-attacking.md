### LeetCode-495-teemo-attacking

> 题目链接

[LeetCode-495-teemo-attacking](https://leetcode-cn.com/problems/teemo-attacking/)

> 思路

遍历数组，寻找中毒时间和前后时间差，取最小值

> 代码

```java
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        if(timeSeries.length == 0) return 0;
        int count = 0;
        int preNumber = timeSeries[0];
        for(int i = 1; i < timeSeries.length; i++){
            count += Math.min(timeSeries[i] - preNumber, duration);
            preNumber = timeSeries[i];
        }
        return count + duration;
    }
}
```

> 复杂度分析

遍历数组一次，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了91.83%的用户

内存消耗：40.2 MB, 在所有 Java 提交中击败了50.99%的用户
