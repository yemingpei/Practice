### LeetCode-offer-42

> 题目链接

[LeetCode-offer-42](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

> 思路

动态规划 f(n) = Math.max(max, f(n - 1) + nums[n])

> 代码

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = nums[0];
        int former = 0;
        int cur = nums[0];
        for (int num : nums) {
            cur = num;
            if (former > 0) cur += former;
            if (cur > max) max = cur;
            former = cur;
        }
        return max;
    }
}
```

> 复杂度分析

遍历一次数组，时间复杂度O(n)

额外使用三个int值，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.36%的用户

内存消耗：44.9 MB, 在所有 Java 提交中击败了66.30%的用户
