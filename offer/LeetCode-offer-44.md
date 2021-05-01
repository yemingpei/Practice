### LeetCode-offer-44

> 题目链接

[LeetCode-offer-44](https://leetcode-cn.com/problems/shu-zi-xu-lie-zhong-mou-yi-wei-de-shu-zi-lcof/)

> 思路

分成0到9，10到99，100到999，先计算出在多少为数上，然后计算出第n位是什么数字，再定位这个数字的第几个

> 代码

```java
class Solution {
    public int findNthDigit(int n) {
        int digit = 1;
        long start = 1;
        long count = 9;
        while (n > count) {
            n -= count;
            digit += 1;
            start *= 10;
            count = digit * start * 9;
        }
        long num = start + (n - 1) / digit;
        return Long.toString(num).charAt((n - 1) % digit) - '0';
    }
}
```

> 复杂度分析

不断乘以10，时间复杂度O(logn)

额外使用int常量辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.2 MB, 在所有 Java 提交中击败了72.38%的用户
