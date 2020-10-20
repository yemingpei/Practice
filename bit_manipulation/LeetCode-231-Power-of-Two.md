### LeetCode-231-Power-of-Two

> 题目链接

[LeetCode-231-Power-of-Two](https://leetcode.com/problems/power-of-two/)

> 思路

二进制是否只包含一个1，可以通过（消除最右边的1）(n & (n - 1)) == 0或者（获取最右边的1） (n & -n) == n来判断

> 代码

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if(n <= 0) return false;
        return (n & (n - 1)) == 0;
    }
}
```

> 复杂度分析

位运算求解是否只有一个1，时间复杂度O(1)

无额外使用其他变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Power of Two.

Memory Usage: 35.8 MB, less than 12.03% of Java online submissions for Power of Two.
