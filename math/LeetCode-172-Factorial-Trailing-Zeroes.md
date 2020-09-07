### LeetCode-172-Factorial-Trailing-Zeroes

> 题目链接

[LeetCode-172-Factorial-Trailing-Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/)

> 思路

求n！，十进制有多少个0，其实就是求有多少个5，求5的因子的个数，比如25是两个5，125是三个5，所以result = n / 5 + n / 25 + n / 125 + n / 625······ 

> 代码

```java
class Solution {
    public int trailingZeroes(int n) {
        int result = 0;
        while(n != 0){
            n = n / 5;
            result += n;
        }
        return result;
    }
}
```

> 复杂度分析

不断除5，时间复杂度O(logn)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Factorial Trailing Zeroes.

Memory Usage: 36.1 MB, less than 95.90% of Java online submissions for Factorial Trailing Zeroes.
