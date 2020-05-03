### LeetCode-57-Insert-Interval

> 题目链接

[LeetCode-57-Insert-Interval](https://leetcode.com/problems/insert-interval/)

> 思路

先插入需要插入的数据，再遍历看看是否需要合并

> 代码

```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        int row = intervals.length;
        int[][] newSet = new int[row + 1][2];
        int[][] result = new int[row + 1][2];
        boolean flag = false;
        int n = 0;
        for (int i = 0; i < row; i++) {
          if (flag || intervals[i][0] < newInterval[0]) {
            newSet[n] = intervals[i];
            n++;
          } else {
            flag = true;
            newSet[n] = newInterval;
            newSet[n + 1] = intervals[i];
            n = n + 2;
          }
        }
        if (!flag)
          newSet[row] = newInterval;
        int count = 0;
        int max = newSet[0][1];
        result[0][0] = newSet[0][0];
        for (int i = 1; i < row + 1; i++) {
          if (max >= newSet[i][0]) {
            max = Math.max(max, newSet[i][1]);
          } else {
            result[count][1] = max;
            count++;
            result[count][0] = newSet[i][0];
            max = newSet[i][1];
          }
        }
        result[count][1] = max;
        count++;
        return Arrays.copyOfRange(result, 0, count);
    }
}
```

> 复杂度分析

遍历两边数组，第一遍，插入数据，第二遍判断是否需要合并，时间复杂度O(n)

额外使用了2个n长度的数组，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 98.23% of Java online submissions for Insert Interval.
Memory Usage: 41.6 MB, less than 71.88% of Java online submissions for Insert Interval.
