### LeetCode-56-Merge-Intervals

> 题目链接

[LeetCode-56-Merge-Intervals](https://leetcode.com/problems/merge-intervals/)

> 思路

先分别用左右边界排序，然后就比较左右边界的大小关系，确定新的边界

> 代码

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        int row = intervals.length;
        int[] starts = new int[row];
        int[] ends = new int[row];
        for (int i = 0; i < row; i++) {
            starts[i] = intervals[i][0];
            ends[i] = intervals[i][1];
        }
        Arrays.sort(starts);
        Arrays.sort(ends); 
        int[][] result = new int[row][2];
        int count =0;
        for (int i = 0, j = 0; i < row; i++) { 
            if (i == row - 1 || starts[i + 1] > ends[i]) {
            	result[count++]=new int[]{starts[j], ends[i]};
            	j = i + 1;
            }
        }
        return Arrays.copyOfRange(result,0,count);
    }
}
```

> 复杂度分析

先分左边界和右边界排序，然后在遍历合并，时间复杂度O(nlgn)

额外使用了两个数组，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Merge Intervals.
Memory Usage: 42.3 MB, less than 48.55% of Java online submissions for Merge Intervals.
