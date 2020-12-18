### LeetCode-338-Counting-Bits

> 题目链接

[LeetCode-338-Counting-Bits](https://leetcode.com/problems/counting-bits/)

> 思路

i & (i - 1)消除最右边的1，这样i 和 i & (i - 1)的1的位数就相差1.

> 代码

```java
class Solution {
    public int[] countBits(int num) {
        int[] result = new int[num + 1];
        for(int i = 1;i < result.length; i++){
            result[i] = result[i & (i - 1)] + 1;
        }
        return result;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.65% of Java online submissions for Counting Bits.

Memory Usage: 42.8 MB, less than 92.76% of Java online submissions for Counting Bits.
