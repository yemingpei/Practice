### LeetCode-600-non-negative-integers-without-consecutive-ones

> 题目链接

[LeetCode-600-non-negative-integers-without-consecutive-ones](https://leetcode-cn.com/problems/non-negative-integers-without-consecutive-ones/)

> 思路

通过分析二进制位数来得出结果，不能有连续的1

> 代码

```java
class Solution {
    public int findIntegers(int n) {
        int[] dp = new int[31];
        dp[0] = dp[1] = 1;
        for (int i = 2; i < 31; ++i) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        int pre = 0, res = 0;
        for (int i = 29; i >= 0; --i) {
            int val = 1 << i;
            if ((n & val) != 0) {
                res += dp[i + 1];
                if (pre == 1) break;
                pre = 1;
            } else pre = 0;
            if (i == 0) ++res;
        }
        return res;
    }
}
```

> 复杂度分析

遍历二进制的位数，时间复杂度O(logn)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.7 MB, 在所有 Java 提交中击败了22.69%的用户
