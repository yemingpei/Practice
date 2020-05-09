### LeetCode-875-Koko-Eating-Bananas

> 题目链接

[LeetCode-875-Koko-Eating-Bananas](https://leetcode.com/problems/koko-eating-bananas/)

> 思路

用数组的和，除以时间H可以得出二分的范围的最小值，max为二分的最大值，通过不断计算K值，寻找最小的k

> 代码

```java
class Solution {
    public int minEatingSpeed(int[] piles, int H) {
        int max = 1;
        int total = 0;
        for (int i : piles) {
            max = Math.max(max, i);
            total += i;
        }
        if (H == piles.length) return max;
        int min = Math.max(total / H, 1);
        while (max > min) {
            int mid = min + ((max - min) >> 1);
            if (wise(piles, H, mid)) {
                max = mid;
            } else {
                min = mid + 1;
            }
        }
        return max;
    }

    public boolean wise(int[] piles, int H, int k) {
        int sum = 0;
        for (int i : piles) {
            sum += (i-1) / k + 1;
        }
        return sum <= H;
    }
}
```

> 复杂度分析

利用二分缩小要寻找的值，每次都需要遍历一遍计算用的时间，时间复杂度O(nlgn)

额外使用了sum,min,max,mid等几个int类型的变量,空间复杂度O(1)

> 总结

Runtime: 5 ms, faster than 98.31% of Java online submissions for Koko Eating Bananas.

Memory Usage: 40.2 MB, less than 100.00% of Java online submissions for Koko Eating Bananas.
