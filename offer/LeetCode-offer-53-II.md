### LeetCode-offer-53-II

> 题目链接

[LeetCode-offer-53-II](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

> 思路

利用二分查找，寻找左边第一个nums[i] != i的数字

> 代码

```java
class Solution {
    public int missingNumber(int[] nums) {
        return findNumber(nums, 0, nums.length - 1);
    }

    public int findNumber(int[] nums, int left, int right){
        if(left == right) return nums[left] == left ? left + 1 : left;
        int mid = left + (right - left) / 2;
        if(nums[mid] == mid) return findNumber(nums, mid + 1, right);
        else return findNumber(nums, left, mid);
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(logn)

额外使用指针来辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了45.88%的用户
