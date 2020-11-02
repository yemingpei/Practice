### LeetCode-191-Number-of-1-Bits

> 题目链接

[LeetCode-191-Number-of-1-Bits](https://leetcode.com/problems/number-of-1-bits/)

> 思路

二进制是否包含的个数，可以通过（消除最右边的1）(n & (n - 1)) == 0 或者（获取最右边的1） (n & -n) == n 是否存在来判断

> 代码

```java
public class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while(n != 0){
            n &= (n - 1);
            count++;
        }
        return count;
    }
}
```

> 复杂度分析

最多32个1，时间复杂度O(1)

无额外使用其他变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Number of 1 Bits.

Memory Usage: 36.1 MB, less than 6.01% of Java online submissions for Number of 1 Bits.
