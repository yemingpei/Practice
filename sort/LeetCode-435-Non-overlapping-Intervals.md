### LeetCode-435-Non-overlapping-Intervals

> 题目链接

[LeetCode-435-Non-overlapping-Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

> 思路

通过贪心算法，寻找左边相同，且右边尽可能小，分成较多的小块，能满足题意

> 代码

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if(intervals == null || intervals.length <= 1) return 0;
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        int end = intervals[0][1];
        int result = 0;
        for(int i = 1; i < intervals.length; i++) {
            if(intervals[i][0] < end) {
                end = Math.min(end, intervals[i][1]);
                result++;
            } else {
                end = intervals[i][1];
            }
        }
        return result;
    }
}
```

> 复杂度分析

需要排序，时间复杂度O(nlogn)

额外使用常数个int，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Non-overlapping Intervals.

Memory Usage: 38.9 MB, less than 75.22% of Java online submissions for Non-overlapping Intervals.
