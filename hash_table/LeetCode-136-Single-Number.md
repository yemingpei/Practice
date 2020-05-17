### LeetCode-136-Single-Number

> 题目链接

[LeetCode-136-Single-Number](https://leetcode.com/problems/single-number/)

> 思路

使用位运算，相同的数异或为0，0异或任何数为任何数

> 代码

```java
class Solution {
    public int singleNumber(int[] nums) {
        int num = 0;
        for (int i : nums)
          num ^= i;
        return num;
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，时间复杂度O(n)

空间复杂度O(1)

> 总结
Runtime: 0 ms, faster than 100.00% of Java online submissions for Single Number.

Memory Usage: 40.7 MB, less than 76.30% of Java online submissions for Single Number.
