### LeetCode-152-Maximum-Product-Subarray

> 题目链接

[LeetCode-152-Maximum-Product-Subarray](https://leetcode.com/problems/maximum-product-subarray/)

> 思路

保存最小值，和最大值，当遇到负数，则交换两个值。

> 代码

```java
class Solution {
    public int maxProduct(int[] nums) {
        int max = Integer.MIN_VALUE, imax = 1, imin = 1;
        for (int i = 0; i < nums.length; i++) {
            if(nums[i] < 0){
                int temp = imin;
                imin = imax;
                imax = temp;
            }
            imax = Math.max(imax*nums[i], nums[i]);
            imin = Math.min(imin*nums[i], nums[i]);
            max = Math.max(max, imax);
        }
        return max;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

需要两个常量int来记录最小值和最大值，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 95.24% of Java online submissions for Maximum Product Subarray.

Memory Usage: 39.4 MB, less than 82.24% of Java online submissions for Maximum Product Subarray.
