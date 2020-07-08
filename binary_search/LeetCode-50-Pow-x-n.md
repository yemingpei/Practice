### LeetCode-50-Pow(x, n)

> 题目链接

[LeetCode-50-Pow(x, n)](https://leetcode.com/problems/powx-n/)

> 思路

比如 2 ^ 4 = (2 ^ 2) ^ 2,不断做内平方，减少相乘的次数

> 代码

```java
class Solution {
    public double myPow(double x, int n) {
        if(n == 0) return 1;
        double h = myPow(x, n / 2);
        if(n % 2 == 0)
            return h * h;
        else if(n > 0)
            return h * h * x;
        else
            return h * h / x;
    }
}
```

> 复杂度分析

不断平方减少相乘的次数，时间复杂度O(lgn)

额外使用double，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100% of Java online submissions for Pow(x, n).

Memory Usage: 38.7 MB, less than 8.27% of Java online submissions for Pow(x, n).
