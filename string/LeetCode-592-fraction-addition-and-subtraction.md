### LeetCode-592-fraction-addition-and-subtraction

> 题目链接

[LeetCode-592-fraction-addition-and-subtraction](https://leetcode-cn.com/problems/fraction-addition-and-subtraction/)

> 思路

通过公倍数，计算全部的和，再约分

> 代码

```java
class Solution {
    public String fractionAddition(String expression) {
        char[] chars = expression.toCharArray();
        char sign = chars[0] == '-' ? '-' : '+', c;
        int i = (chars[0] == '-' || chars[0] == '+') ? 1 : 0;
        int num = 0, denominator = 1, numerator = 0, curDma = 0, curNmr = 0, lcm;
        for (; i < chars.length; ++i) {
            c = chars[i];
            if (c == '+' || c == '-') {
                curDma = num;
                lcm = denominator * curDma / gcd(denominator, curDma);
                numerator *= lcm / denominator;
                denominator = lcm;
                curNmr *= lcm / curDma;
                if (sign == '+') {
                    numerator += curNmr;
                }else {
                    numerator -= curNmr;
                }
                sign = c;
                num = 0;
            }else if (c == '/') {
                curNmr = num;
                num = 0;
            }else {
                num = num * 10 + c - '0';
            }
        }
        curDma = num;
        lcm = denominator * curDma / gcd(denominator, curDma);
        numerator *= lcm / denominator;
        denominator = lcm;
        curNmr *= lcm / curDma;
        if (sign == '+') {
            numerator += curNmr;
        }else {
            numerator -= curNmr;
        }
        if (numerator == 0) {
            return "0/1";
        }
        StringBuilder sb = new StringBuilder();
        if (numerator < 0) {
            numerator = -numerator;
            sb.append('-');
        }
        int gcd = gcd(denominator, numerator);
        sb.append((numerator / gcd)).append('/').append((denominator / gcd));
        return sb.toString();
    }

    private int gcd(int a, int b) {
        if (a == 0 || b == 0) {
            return 0;
        }
        int c;
        while (b != 0) {
            c = a % b;
            a = b;
            b = c;
        }
        return a;
    }
}
```

> 复杂度分析

遍历字符，通过公倍数计算，时间复杂度O(nlogn)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.6 MB, 在所有 Java 提交中击败了94.61%的用户
