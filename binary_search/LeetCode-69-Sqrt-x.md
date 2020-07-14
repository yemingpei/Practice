### LeetCode-69-Sqrt(x)

> 题目链接

[LeetCode-69-Sqrt(x)](https://leetcode.com/problems/sqrtx/)

> 思路

利用二分法，不断缩小开方的数值

> 代码

```java
class Solution {
    public int mySqrt(int x) {
        if (x <= 1) return x;
        int i = 2, j = x / 2;
        while (i <= j) {
            int mid = i + (j - i) / 2;
            long value = (long) mid * (long) mid;
            if (value > x) j = mid - 1;
            else if (value < x) i = mid + 1;
            else return mid;
        }
        return j;
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(lgn)

额外使用int来记录边界，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100% of Java online submissions for Sqrt(x).

Memory Usage: 36.8 MB, less than 51.81% of Java online submissions for Sqrt(x).
