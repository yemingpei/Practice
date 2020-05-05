### LeetCode-81-Search-in-Rotated-Sorted-Array-II

> 题目链接

[LeetCode-81-Search-in-Rotated-Sorted-Array-II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

> 思路

```java
//例子1：4 5 1 2 3  寻找4，右边是顺序
//例子2：4 5 6 2 3  寻找2，左边是顺序
//例子3：1 2 1 1 1  寻找2，相同的数据比较多，不能单独比较mid和low或者high和mid，从左边开始逐个比较
```
上述例子1，右边是顺序，4不在右边的范围，就可以判断在左边，例子2同理，例子3则之恩那个一个一个判断，所以最坏情况是O(n)，其他case都是O(lgn)

> 代码

```java
class Solution {
    public boolean search(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;
        while (high >= low) {
          int mid = low + ((high - low) >> 1);
          if (nums[mid] == target) return true;
          else if (nums[mid] > nums[low]) {
            if (nums[mid] > target && target >= nums[low])
              high = mid - 1;
            else
              low = mid + 1;
          } else if (nums[mid] < nums[high]) {
            if (nums[mid] < target && target <= nums[high])
              low = mid + 1;
            else
              high = mid - 1;
          } else if(nums[low] == target)
            return true;
          else
            low++;
        }
        return false;
    }
}
```

> 复杂度分析

二分查找，因为是逆向顺序，所以从中间开始分，肯定会有另一边是有序的，然后逐渐有序，时间复杂度是O(lgn)，最坏情况还是时间复杂度O(n)

额外使用了高位，低位，中位置三个辅助int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Search in Rotated Sorted Array II.

Memory Usage: 39 MB, less than 76.06% of Java online submissions for Search in Rotated Sorted Array II.
