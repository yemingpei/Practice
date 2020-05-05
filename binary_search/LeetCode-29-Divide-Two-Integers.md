### LeetCode-29-Divide-Two-Integers

> 题目链接

[LeetCode-29-Divide-Two-Integers](https://leetcode.com/problems/divide-two-integers/)

> 思路

（如下论述的，被除数和除数都是绝对值）如果被除数小于除数，直接返回0，溢出只有在除数绝对值为1的时候才有可能出现，当被除数大于除数时候，商至少为1，
如果除数 * 2,还比被除数大，那商至少为 2，一次类推，寻找除数不断 * 2比被除数刚刚小的商，被除数减去上述找到的值，继续循环，和小学画的除法草稿一致。

> 代码

```java
class Solution {
    public int divide(int dividend, int divisor) {
        if (dividend == 0) return 0;
        boolean signal = (dividend ^ divisor) >= 0;
        long a = Math.abs((long)dividend);
        long b = Math.abs((long)divisor);
        if (b > a) return 0;
        int sum = 0;
        if (b == 1) {
          if (signal && a > Integer.MAX_VALUE)
            return Integer.MAX_VALUE;
                else
                    return signal ? (int)a : -(int)a;
        } else {
          while (a >= b) {
            long c = b;
            long result = 1;
            while (a >= c) {
              c = c << 1;
              result = result << 1;
            }
            sum = sum + (int)(result >> 1);
            a = a - (c >> 1);
          }
        }
        return signal ? sum : -sum;
    }
}
```

> 复杂度分析

不断左移，使用二分思想，寻找值，时间复杂度O(lgn)

额外使用a,b,c三个long类型，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Divide Two Integers.

Memory Usage: 37.1 MB, less than 6.06% of Java online submissions for Divide Two Integers.
