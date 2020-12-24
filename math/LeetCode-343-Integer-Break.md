### LeetCode-343-Integer-Break

> 题目链接

[LeetCode-343-Integer-Break](https://leetcode.com/problems/integer-break/)

> 思路

计算n包含多少个3，分成的值越接近e，乘积越大

> 代码

```java
class Solution {
    public int integerBreak(int n) {
        if(n < 4) return n - 1;
        int remainder = n % 3;
        int quotient = n / 3;
        if(remainder == 0) return (int) Math.pow(3, quotient);
        if(remainder == 1) return (int) Math.pow(3, quotient - 1) * 4;
        return (int) Math.pow(3, quotient) * 2;
    }
}
```

> 复杂度分析

幂函数，时间复杂度O(1)

额外使用两个int来表示商和余数，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Integer Break.

Memory Usage: 35.5 MB, less than 85.38% of Java online submissions for Integer Break.
