### LeetCode-268-Missing-Number

> 题目链接

[LeetCode-268-Missing-Number](https://leetcode.com/problems/missing-number/)

> 思路

利用异或运算，两个相同的数异或消除，注意初始值为nums.length，可以利用数组循环，避开多余的操作

> 代码

```java
class Solution {
    public int missingNumber(int[] nums) {
        int number = nums.length;
        for (int i = 0; i < nums.length; i++) {
            number ^= i ^ nums[i];
        }
        return number;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用其他变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Missing Number.

Memory Usage: 39.6 MB, less than 5.66% of Java online submissions for Missing Number.
