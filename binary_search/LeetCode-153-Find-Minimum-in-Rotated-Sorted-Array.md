### LeetCode-153-Find-Minimum-in-Rotated-Sorted-Array

> 题目链接

[LeetCode-153-Find-Minimum-in-Rotated-Sorted-Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

> 思路
```java
//例子1  1 2 3 4 5 最小值应该在最前面
//例子2  2 3 4 5 1 最小值应该在最后面
//例子3  3 4 5 1 2 最小值在中间
```

利用中间值的特点，不断缩小峰值的范围，注意二分的循环判断，非左即右，利用题目给得相邻的数字不相等。

> 代码

```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        while(right >= left){
            if(left == right) return nums[left];
            else if(nums[left] > nums[right]){
                int middle = (left + right) >> 1;
                if(nums[left] <= nums[middle]) left = middle + 1;
                else right = middle;
            }else return nums[left]; 
        }
        return 0;
    }
}
```

> 复杂度分析

不断利用中点缩小峰值的范围，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Find Minimum in Rotated Sorted Array.

Memory Usage: 39.3 MB, less than 52.46% of Java online submissions for Find Minimum in Rotated Sorted Array.
