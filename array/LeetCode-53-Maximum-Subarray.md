### LeetCode-53-Maximum-Subarray

> 题目链接

[LeetCode-53-Maximum-Subarray](https://leetcode.com/problems/maximum-subarray/)

> 思路

遍历一遍数组，数值用HashMap保存起来，如果找到target - 对应位置差值的数，则输出位置

> 代码

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        int sum = 0;
        for(int number:nums){
            sum = sum + number;
            max = Math.max(max,sum);
            if(sum < 0) sum = 0;
        }
        return max;
    }
}
```

> 复杂度分析

遍历了一遍数组nums，时间复杂度O(n)

额外使用了sum和max的辅助指针，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Maximum Subarray.

Memory Usage: 39.6 MB, less than 35.90% of Java online submissions for Maximum Subarray.
