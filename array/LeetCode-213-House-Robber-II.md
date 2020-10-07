### LeetCode-213-House-Robber-II

> 题目链接

[LeetCode-213-House-Robber-II](https://leetcode.com/problems/house-robber-ii/)

> 思路

因为前后形成环，所以首尾，只能取一个，分别计算如果取了头，间隔取值的最大值，取尾，间隔取值的最大值，比较取最大就是最大的收益

> 代码

```java
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 0) return 0;
        if(nums.length == 1) return nums[0];
        return Math.max(myRob(nums, 0, nums.length - 2),
                       myRob(nums, 1, nums.length - 1));
    }
     private int myRob(int[] nums, int start, int end) {
        int pre = 0, cur = 0, tmp;
        for(int i = start; i <= end; i++) {
            tmp = cur;
            cur = Math.max(pre + nums[i], cur);
            pre = tmp;
        }
        return cur;
    }
}
```

> 复杂度分析

遍历2遍数组，时间复杂度O(n)

需要临时变量来记录计算的量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for House Robber II.

Memory Usage: 36.4 MB, less than 94.07% of Java online submissions for House Robber II.
