### LeetCode-offer-53-I

> 题目链接

[LeetCode-offer-53-I](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

> 思路

利用二分查找，先寻找头和尾巴，然后利用首尾position来计算个数

> 代码

```java
class Solution {
    public int search(int[] nums, int target) {
        if(nums.length == 0) return 0;
        int left = searchLeft(nums, target, 0, nums.length - 1);
        if(left == -1) return 0;
        int right = searchRight(nums, target, 0, nums.length - 1);
        return right - left + 1;
    }

    public int searchLeft(int[] nums, int target, int left, int right) {
        if(left == right){
            return nums[left] == target ? left : -1;
        }
        int mid = left + (right - left) / 2;
        if(nums[mid] < target) return searchLeft(nums, target, mid + 1, right);
        else return searchLeft(nums, target, left, mid);
    }

    public int searchRight(int[] nums, int target, int left, int right) {
        if(left == right){
            return nums[left] == target ? left : -1;
        }
        int mid = right - (right - left) / 2;
        if(nums[mid] > target) return searchRight(nums, target, left, mid - 1);
        else return searchRight(nums, target, mid, right);
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(logn)

额外使用指针来辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：41.3 MB, 在所有 Java 提交中击败了61.43%的用户
