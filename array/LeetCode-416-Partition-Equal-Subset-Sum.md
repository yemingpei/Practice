### LeetCode-416-Partition-Equal-Subset-Sum

> 题目链接

[LeetCode-416-Partition-Equal-Subset-Sum](https://leetcode.com/problems/partition-equal-subset-sum/)

> 思路

寻找两个和相同的子数组，必然数组的和是偶数，最大的数不大于总和的一半，才存在，然后深度遍历，寻找和

> 代码

```java
class Solution {
    public boolean dfs(int[] nums, int target, int sum , int idx, boolean[] cache) {
        if(idx >= nums.length) {
            return false;
        }
        
        if(sum + nums[idx] == target) {
            return true;
        }
        
        if(sum + nums[idx] <= target && !cache[sum + nums[idx]]) {
            cache[sum + nums[idx]] = true;
            if(dfs(nums, target, sum + nums[idx], idx+1, cache)) {
                return true;
            }
        }
        
        if(dfs(nums, target, sum, idx+1, cache)) {
            return true;
        }
        
        return false;
    }
    
    public boolean canPartition(int[] nums) {
        if(nums == null || nums.length == 0) {
            return false;
        }
        
        int sum = 0;
        for (int num: nums) {
            sum += num;
        }

        if (sum % 2 == 1) {
            return false;
        }

        sum = sum / 2;

        boolean[] cache = new boolean[sum+1];
        
        return dfs(nums, sum, 0, 0, cache);
    }
}
```

> 复杂度分析

深度遍历，有剪枝，时间复杂度O(n ^ 2)

额外boolean数组，空间复杂度O(n)。

> 总结

Runtime: 1 ms, faster than 99.86% of Java online submissions for Partition Equal Subset Sum.

Memory Usage: 38.6 MB, less than 80.89% of Java online submissions for Partition Equal Subset Sum.
