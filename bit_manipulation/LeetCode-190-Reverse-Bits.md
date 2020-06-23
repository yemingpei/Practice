### LeetCode-190-Reverse-Bits

> 题目链接

[LeetCode-190-Reverse-Bits](https://leetcode.com/problems/reverse-bits/)

> 思路

不断寻找1的位置，然后进行反转，i对应反转位为31 - i

> 代码

```java
public class Solution {
    public int reverseBits(int n) {
        int sum = 0;
        for(int i = 0; i < 32; i++){
            int number = 1 << i;
            if((number & n) == number) sum = sum | (1 << (31 - i));
        }
        return sum;
    }
}
```

> 复杂度分析

执行32次，时间复杂度O(1)

额外使用有int辅助指针，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.54% of Java online submissions for Reverse Bits.

Memory Usage: 39.3 MB, less than 34.59% of Java online submissions for Reverse Bits.
