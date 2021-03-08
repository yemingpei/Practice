### LeetCode-476-Number-Complement

> 题目链接

[LeetCode-476-Number-Complement](https://leetcode.com/problems/number-complement/)

> 思路

用位运算用每一个1做异或，反转原来的每一位

> 代码

```java
class Solution {
    public int findComplement(int num) {
        int mask = 1;
        int comp = num;
        while (num != 0) {
            comp ^= mask;
            mask <<= 1;
            num >>= 1;
        }
        return comp;
    }
}
```

> 复杂度分析

位运算，最多32次，时间复杂度O(1)

额外使用int常量来辅助，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Number Complement.

Memory Usage: 35.4 MB, less than 98.81% of Java online submissions for Number Complement.
