### LeetCode-offer-16

> 题目链接

[LeetCode-offer-16](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

> 思路

利用不断平方来接近答案的数，注意负数最小值的时候转正数溢出的问题

> 代码

```java
class Solution {
    public double myPow(double x, int n) {
        if (n == 0){
            return 1.0;
        }
        if (n < 0){
            return myPow(1.0 / x,-(n + 1)) * (1.0 / x);
        }else {
            if (n % 2 == 0){
                return myPow(x * x,n / 2);
            }else {
                return myPow(x * x,n / 2) * x;
            }
        }
    }
}
```

> 复杂度分析

不断平方，时间复杂度O(logn)

额外使用递归函数栈，空间复杂度O(logn)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.47%的用户

内存消耗：37.7 MB, 在所有 Java 提交中击败了56.39%的用户

