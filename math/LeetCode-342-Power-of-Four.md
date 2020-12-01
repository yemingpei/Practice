### LeetCode-342-Power-of-Four

> 题目链接

[LeetCode-342-Power-of-Four](https://leetcode.com/problems/power-of-four/)

> 思路

先判断二进制位是否只有一个1，然后判断除以3余数是否为1，因为(2 ^ 2k) % 3 = ( 4 ^ k) % 3 = (3 + 1) ^ k % 3 = 3 * (3 + 1) ^ (k - 1) % 3 + (3 + 1) ^ (k - 1) % 3 ,化简得（3 + 1） ^ 0 % 3 = 1

> 代码

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        return n > 0 && (n & (n - 1)) == 0 && n % 3 == 1; 
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.33% of Java online submissions for Power of Four.

Memory Usage: 36.1 MB, less than 49.67% of Java online submissions for Power of Four.
