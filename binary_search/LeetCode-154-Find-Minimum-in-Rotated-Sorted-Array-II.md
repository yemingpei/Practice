### LeetCode-154-Find-Minimum-in-Rotated-Sorted-Array-II

> 题目链接

[LeetCode-154-Find-Minimum-in-Rotated-Sorted-Array-II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

> 思路

因为该序列必然一半有序，利用这个来判断，最小值在左边还是右边，来实现二分查找

> 代码

```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        int mid = 0;
        while(left < right){
            if(nums[left] < nums[right])
                return nums[left];
            else if(nums[left] == nums[right])
                    left++;
            else{
                mid = left + ((right - left) >> 1);
                if(nums[left] <= nums[mid])
                    left = mid + 1;
                else if(nums[mid] <= nums[right])
                    right = mid;
            }
        }
        if(left == right)
            return nums[left];
        else
            return 0;
    }
}
```

> 复杂度分析

不断利用中点缩小峰值的范围，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Find Minimum in Rotated Sorted Array II.

Memory Usage: 39.5 MB, less than 54.85% of Java online submissions for Find Minimum in Rotated Sorted Array II.
