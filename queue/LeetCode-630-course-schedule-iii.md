### LeetCode-630-course-schedule-iii

> 题目链接

[LeetCode-630-course-schedule-iii](https://leetcode-cn.com/problems/course-schedule-iii/)

> 思路

先利用最晚时间排序，然后利用堆，没个大于要求时间的时候，吐出需要最大时间的值

> 代码

```java
class Solution {
    public int scheduleCourse(int[][] courses) {
        int total = 0;
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>((a, b) -> (b - a));
        Arrays.sort(courses, (a, b) -> (a[1] - b[1]));
        for (int[] course : courses) {
            int time = course[0];
            int ddl = course[1];
            if (total + time <= ddl) {
                priorityQueue.add(time);
                total += time;
            } else {
                if (!priorityQueue.isEmpty() && priorityQueue.peek() >= time) {
                    total -= (priorityQueue.poll() - time);
                    priorityQueue.add(time);
                }
            }
        }
        return priorityQueue.size();
    }
}
```

> 复杂度分析

排序，再遍历数组，时间复杂度O(nlogn)

额外使用堆，空间复杂度O(n)

> 总结

执行用时：31 ms, 在所有 Java 提交中击败了89.13%的用户

内存消耗：46.6 MB, 在所有 Java 提交中击败了33.48%的用户
