### LeetCode-475-heaters

> 题目链接

[LeetCode-475-heaters](https://leetcode-cn.com/problems/heaters/)

> 思路

利用快慢指针，要剔除重复的元素

> 代码

```java
class Solution {
    public int findRadius(int[] houses, int[] heaters) {
        int maxDis = 0;
        int j = 0;
        Arrays.sort(houses);
        Arrays.sort(heaters);
        for (int i = 0; i < houses.length; i++) {
            while (j < heaters.length - 1 && heaters[j + 1] < houses[i]) {
                j++;
            }
            int minDis = abs(houses[i] - heaters[j]);
            if (j < heaters.length - 1) {
                int minDis2 = abs(houses[i] - heaters[j + 1]);
                minDis = minDis > minDis2 ? minDis2 : minDis;
            }
            maxDis = maxDis < minDis ? minDis : maxDis;
        }
        return maxDis;
    }

    int abs(int a) {
        return a > 0 ? a : -a;
    }
}
```

> 复杂度分析

排序消耗时间，时间复杂度O(nlogn)

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：8 ms, 在所有 Java 提交中击败了90.62%的用户

内存消耗：41.6 MB, 在所有 Java 提交中击败了59.02%的用户
