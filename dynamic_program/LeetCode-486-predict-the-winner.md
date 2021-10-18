### LeetCode-486-predict-the-winner

> 题目链接

[LeetCode-486-predict-the-winner](https://leetcode-cn.com/problems/predict-the-winner/)

> 思路

动态规划公式：dp[j] = Math.max(nums[i] - dp[j], nums[j] - dp[j - 1])

> 代码

```java
class Solution {
    public boolean PredictTheWinner(int[] nums) {
        int length = nums.length;
        int[] dp = new int[length];
        for (int i = 0; i < length; i++) {
            dp[i] = nums[i];
        }
        for (int i = length - 2; i >= 0; i--) {
            for (int j = i + 1; j < length; j++) {
                dp[j] = Math.max(nums[i] - dp[j], nums[j] - dp[j - 1]);
            }
        }
        return dp[length - 1] >= 0;
    }
}
```

> 复杂度分析

双重循环，时间复杂度O(n ^ 2)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了12.19%的用户
