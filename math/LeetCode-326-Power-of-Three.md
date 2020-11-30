### LeetCode-326-Power-of-Three

> 题目链接

[LeetCode-326-Power-of-Three](https://leetcode.com/problems/power-of-three/)

> 思路

1162261467是int32位里面3的最高幂次的数，若能被此数整除，则是3的幂次

> 代码

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 10 ms, faster than 99.97% of Java online submissions for Power of Three.

Memory Usage: 38.9 MB, less than 40.62% of Java online submissions for Power of Three.
