### LeetCode-233-Number-of-Digit-One

> 题目链接

[LeetCode-233-Number-of-Digit-One](https://leetcode.com/problems/number-of-digit-one/)

> 思路

个位上的 ’ 就会出现一次。同样的，每 100100 个数，十位上的1 就会出现一次。这个规律可以用 (n/(i*10))*i(n/(i∗10))∗i 公式来表示。

同时，如果十位上的数是1，那么最后1 的数量要加上 x+1x+1，其中 xx 是个位上的数值。如果十位上的数大于 1，那么十位上为 1 的所有的数都是符合要求的，这时候最后 1 的数量要加 1010。

这个规律可以用公式 {\min(\max((\text{n mod (i*10)} )-i+1,0),i)}min(max((n mod (i*10))−i+1,0),i) 来表示。

> 代码

```java
class Solution {
    public int countDigitOne(int n) {
        int count = 0;
        for (long i = 1; i <= n; i*=10) {
            long divider = i * 10;
            count += (n / divider) * i + Math.min(Math.max(n % divider - i + 1, 0), i);
        }
        return count;
    }
}
```

> 复杂度分析

不断除以10来计算1的个数和修正值，时间复杂度O(logn)

额外使用变量count，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Number of Digit One.

Memory Usage: 37.6 MB, less than 5.18% of Java online submissions for Number of Digit One.
