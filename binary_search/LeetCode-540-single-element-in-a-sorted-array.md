### LeetCode-540-single-element-in-a-sorted-array

> 题目链接

[LeetCode-540-single-element-in-a-sorted-array](https://leetcode-cn.com/problems/single-element-in-a-sorted-array/)

> 思路

因为数组有序，可以通过二分查找，优化查询速度

> 代码

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        while(left < right){
            int mid = left + (right - left) / 2;
            if(mid % 2 ==1){
                mid = mid - 1;
            }
            if(nums[mid] == nums[mid+1]){
                left = mid + 2;
            }else{
                right = mid;
            }
        }
        return nums[left];
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(logn)

额外使用常熟变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：43.6 MB, 在所有 Java 提交中击败了5.00%的用户
