### LeetCode-365-Water-and-Jug-Problem

> 题目链接

[LeetCode-365-Water-and-Jug-Problem](https://leetcode.com/problems/water-and-jug-problem/)

> 思路

两个水壶，能拼出来的水，必然是满一次x或者y，或是倒掉x或者y，则有ax+by=z;因为贝祖定理，ax+by=1，则x和y互质，所以z必须是x和y的最大公约数的倍数，则使用辗转相除法求最大公约数

> 代码

```java
class Solution {
    public boolean canMeasureWater(int x, int y, int z) {
        if(x + y < z) return false;
        if(x ==0 || y == 0)
            return z == 0 || x + y == z;
        return z % gcd(x, y) == 0;
    }
    
    public int gcd(int x, int y){
        int remainder = x % y;
        while(remainder != 0){
            x = y;
            y = remainder;
            remainder = x % y;
        }
        return y;
    }
}
```

> 复杂度分析

辗转相除法求最大公约数，时间复杂度O(log(min(x,y))

无使用额外变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Water and Jug Problem.

Memory Usage: 35.4 MB, less than 98.16% of Java online submissions for Water and Jug Problem.
