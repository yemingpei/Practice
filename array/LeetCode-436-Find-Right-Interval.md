### LeetCode-436-Find-Right-Interval

> 题目链接

[LeetCode-436-Find-Right-Interval](https://leetcode.com/problems/find-right-interval/)

> 思路

先保存原来的位置，然后排序，通过二分查找来凭接的数据

> 代码

```java
class Solution {
    public int[] findRightInterval(int[][] intervals) {
        Map<Integer, Integer> map = new HashMap<>();
        int[] starts = new int[intervals.length];
        int[] res = new int[intervals.length];
        for(int i = 0; i < intervals.length; i++){
            map.put(intervals[i][0], i);
            starts[i] = intervals[i][0];
        }
        Arrays.sort(starts);
        for(int i = 0; i < intervals.length; i++){
            int index = Arrays.binarySearch(starts, intervals[i][1]);
            if(index < 0) index = ~index;
            res[i] = index < starts.length ? map.get(starts[index]) : -1;
        }
        return res;
    }
}
```

> 复杂度分析

排序之后，二分查找，时间复杂度O(nlogn)

额外使用map保存位置，空间复杂度O(n)

> 总结

Runtime: 9 ms, faster than 97.32% of Java online submissions for Find Right Interval.

Memory Usage: 47.4 MB, less than 24.33% of Java online submissions for Find Right Interval.
