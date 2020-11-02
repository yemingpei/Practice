### LeetCode-198-House-Robber

> 题目链接

[LeetCode-198-House-Robber](https://leetcode.com/problems/house-robber/)

> 思路

问题可以拆解为

1. 选择投i房间，那总金额为偷 i - 2 的金额加上i房间
2. 偷i - 1, 不偷i，那就等于偷 i - 1 的金额

动态规划公式dp[i] = Math.max(dp[i - 2] + nums[i], dp[i - 1])，因为只需要输出最大值，所以空间可以节省为只保留两个数

> 代码

```java
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 0) return 0;
        if(nums.length == 1) return nums[0];
        int[] dp = new int[2];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for(int i = 2; i < nums.length; i++){
            int snap = dp[1];
            dp[1] = Math.max(dp[0] + nums[i], dp[1]);
            dp[0] = snap;
        }
        return dp[1];
    }
}
```

> 复杂度分析

遍历一次数组，时间复杂度O(n)

额外使用长度为2的数组，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for House Robber.

Memory Usage: 36.3 MB, less than 24.52% of Java online submissions for House Robber.
