### LeetCode-face-16-17

> 题目链接

[LeetCode-face-16-17](https://leetcode-cn.com/problems/contiguous-sequence-lcci/)

> 思路

动态规划，公式为 result = max(result, max(pre + nums[i], nums[i]))

> 代码

```java
class Solution {
    public int maxSubArray(int[] nums) {
        if(nums.length == 0) return 0;
        int result = nums[0];
        int sum = nums[0];
        for(int i = 1; i < nums.length; i++){
            sum = Math.max(sum + nums[i], nums[i]);
            result = Math.max(result, sum);
        }
        return result;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用常量的int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了89.54%的用户
