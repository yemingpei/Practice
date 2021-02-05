### LeetCode-400-Nth-Digit

> 题目链接

[LeetCode-400-Nth-Digit](https://leetcode.com/problems/nth-digit/)

> 思路

n的值找到n所在的范围是长度len的第几个

> 代码

```java
class Solution {
    public int findNthDigit(int n) {
        int k = 1;
        long numDigits = 9;
        int num = 1;
        while (n > k * numDigits) {
            n -= k * numDigits;
            k++;
            numDigits *= 10;
            num *= 10;
        }
        num += (n - 1) / k;
        String s = Integer.toString(num);
        return s.charAt((n - 1) % k) - '0';
    }
}
```

> 复杂度分析

不断通过乘以10来循环，O(logn)

额外使用三个常量，空间复杂度O(1)。

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Nth Digit.

Memory Usage: 35.9 MB, less than 55.73% of Java online submissions for Nth Digit.
