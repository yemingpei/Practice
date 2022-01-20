### LeetCode-643-maximum-average-subarray-i

> 题目链接

[LeetCode-643-maximum-average-subarray-i](https://leetcode-cn.com/problems/maximum-average-subarray-i/)

> 思路

利用滑动窗口寻找最大的和

> 代码

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int sum = 0;
        for(int i = 0; i < k; i++){
            sum += nums[i];
        }
        int res = sum;
        for(int i = k; i < nums.length; i++){
            sum = sum + nums[i] - nums[i - k];
            res = res > sum ? res : sum;
        }
        return (double)res / (double)k;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：52.1 MB, 在所有 Java 提交中击败了59.31%的用户
