### LeetCode-494-target-sum

> 题目链接

[LeetCode-494-target-sum](https://leetcode-cn.com/problems/target-sum/)

> 思路

动态规划dp[j] += dp[j - nums[i]]，通过不断累加，避免重复计算

> 代码

```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int n = nums.length;
        int sum = 0;
        if(nums == null || nums.length == 0) return 0;
        for(int num : nums) sum += num;
        if((target + sum) % 2 == 1) return 0;
        int size = (target + sum) / 2;
        if(size < 0) size = -size;
        int[] dp = new int[size + 1];
        dp[0] = 1;
        for(int i = 0; i < n; i++){
            for(int j = size; j >= nums[i]; j--){
                dp[j] += dp[j - nums[i]];
            }
        }
        return dp[size];
    }
}
```

> 复杂度分析

双重循环遍历，时间复杂度O(n ^ 2)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了94.63%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了81.15%的用户
