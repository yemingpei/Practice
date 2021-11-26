### LeetCode-539-minimum-time-difference

> 题目链接

[LeetCode-539-minimum-time-difference](https://leetcode-cn.com/problems/minimum-time-difference/)

> 思路

大于1440个点，必有重复，否则就进行排序，依次计算差值

> 代码

```java
class Solution {
    public int findMinDifference(List<String> timePoints) {
        if (timePoints.size() >= 24 * 60)  return 0;
        int [] array = new int[timePoints.size()];
        for (int i = 0; i < timePoints.size(); i++) {
            String timePoint = timePoints.get(i);
            int hours = timePoint.charAt(0) * 10 * 60 + timePoint.charAt(1) * 60;
            int minutes = timePoint.charAt(3) * 10 + timePoint.charAt(4);
            array[i] = hours + minutes;
        }
        Arrays.sort(array);
        int min = Integer.MAX_VALUE;
        for (int i = 0; i < array.length - 1; i++) min = Math.min(min, array[i +1] - array[i]);
        return Math.min(min, 24 * 60 + array[0] - array[array.length - 1]);
    }
}
```

> 复杂度分析

因为个数少于1440个，时间复杂度O(1)

额外使用数组，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了78.14%的用户
