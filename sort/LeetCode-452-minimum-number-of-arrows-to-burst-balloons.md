### LeetCode-452-minimum-number-of-arrows-to-burst-balloons

> 题目链接

[LeetCode-452-minimum-number-of-arrows-to-burst-balloons](https://leetcode-cn.com/problems/minimum-number-of-arrows-to-burst-balloons/)

> 思路

按右边前后顺序排序，从最右边一枪能穿过重叠的部分

> 代码

```java
class Solution {
    public int findMinArrowShots(int[][] points) {
        if (points.length == 0) return 0;
        Arrays.sort(points, (a, b) -> a[1] == b[1] ? 0 : a[1] > b[1] ? 1 : -1);
        int pos = points[0][1];
        int ans = 1;
        for (int[] balloon: points) {
            if (balloon[0] > pos) {
                pos = balloon[1];
                ++ans;
            }
        }
        return ans;
    }
}
```

> 复杂度分析

使用了排序，时间复杂度O(nlogn)

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：55 ms, 在所有 Java 提交中击败了20.11%的用户

内存消耗：69.3 MB, 在所有 Java 提交中击败了11.01%的用户
