### LeetCode-162-Find-Peak-Element

> 题目链接

[LeetCode-162-Find-Peak-Element](https://leetcode.com/problems/find-peak-element/)

> 思路
```java
//例子1  1 2 3 4 5 峰值应该是最后的位置
//例子2  5 4 3 2 1 峰值应该是最开始的位置
//例子3  1 2 3 1 2 峰值应该是数字3所在的位置
```

利用中间值的特点，不断缩小峰值的范围，最后输出峰值，注意二分的循环判断，high > low,不断比较mid和mid的下一个数字，利用题目给得相邻的数字不相等。

> 代码

```java
class Solution {
    public int findPeakElement(int[] nums) {
        int low = 0;
        int high = nums.length - 1;
        while (high > low) {
          int mid = low + ((high - low) >> 1);
          if (nums[mid] > nums[mid + 1])
            high = mid;
          else
            low = mid + 1;
        }
        return low;
    }
}
```

> 复杂度分析

不断利用中点缩小峰值的范围，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Find Peak Element.

Memory Usage: 39.5 MB, less than 64.18% of Java online submissions for Find Peak Element.
