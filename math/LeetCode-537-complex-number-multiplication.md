### LeetCode-537-complex-number-multiplication

> 题目链接

[LeetCode-537-complex-number-multiplication](https://leetcode-cn.com/problems/complex-number-multiplication/)

> 思路

数学法计算复数乘法

> 代码

```java
class Solution {
    public String complexNumberMultiply(String num1, String num2) {
        String x[] = num1.split("\\+|i");
        String y[] = num2.split("\\+|i");
        int a_real = Integer.parseInt(x[0]);
        int a_img = Integer.parseInt(x[1]);
        int b_real = Integer.parseInt(y[0]);
        int b_img = Integer.parseInt(y[1]);
        return (a_real * b_real - a_img * b_img) + "+" + (a_real * b_img + a_img * b_real) + "i";
    }
}
```

> 复杂度分析

使用数学方法计算，时间复杂度O(1)

额外使用常量int，空间复杂度O(1)

> 总结

执行用时：8 ms, 在所有 Java 提交中击败了34.67%的用户

内存消耗：37 MB, 在所有 Java 提交中击败了18.00%的用户
