### LeetCode-201-Bitwise-AND-of-Numbers-Range

> 题目链接

[LeetCode-201-Bitwise-AND-of-Numbers-Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)

> 思路

寻找m 和 n的二进制的公共前缀

> 代码

```java
class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int offset = 0;
        while(m < n){
            m >>= 1;
            n >>= 1;
            offset++;
        }
        return m << offset;
    }
}
```

> 复杂度分析

最多遍历32次，时间复杂度O(1)

额外使用有int数据辅助，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 97.34% of Java online submissions for Bitwise AND of Numbers Range.

Memory Usage: 41.7 MB, less than 5.04% of Java online submissions for Bitwise AND of Numbers Range.
