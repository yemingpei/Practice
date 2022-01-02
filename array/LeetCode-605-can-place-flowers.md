### LeetCode-605-can-place-flowers

> 题目链接

[LeetCode-605-can-place-flowers](https://leetcode-cn.com/problems/can-place-flowers/)

> 思路

通过贪心算法，判断种树的跳动位置

> 代码

```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int i = 0;
        int res = 0;
        while (i < flowerbed.length - 1) {
            if (flowerbed[i + 1] == 1) {
                i = i + 3;
            } else if (flowerbed[i] == 1) {
                i = i + 2;
            } else {
                res++;
                i = i + 2;
            }
        }
        if (i == flowerbed.length - 1 && flowerbed[i] == 0) res++;
        return res >= n;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.9 MB, 在所有 Java 提交中击败了63.64%的用户
