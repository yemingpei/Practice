### LeetCode-376-Wiggle-Subsequence

> 题目链接

[LeetCode-376-Wiggle-Subsequence](https://leetcode.com/problems/wiggle-subsequence/)

> 思路

通过计算两个方向的值，第一次是负，第一次是正，然后开始摇摆，最后输出两个值中的最大值

> 代码

```java
class Solution {
    public int wiggleMaxLength(int[] nums) {
        if (nums.length < 2) {
            return nums.length;
        }
        int up = 1;
        int down = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                up = down + 1;
            } else if (nums[i] < nums[i - 1]) {
                down = up + 1;
            }
        }
        return Math.max(down, up);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要两个常量int来记录两个方向的计数，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Wiggle Subsequence.

Memory Usage: 36.3 MB, less than 93.15% of Java online submissions for Wiggle Subsequence.
