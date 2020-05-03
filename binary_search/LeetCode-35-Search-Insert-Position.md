### LeetCode-35-Search-Insert-Position

> 题目链接

[LeetCode-35-Search-Insert-Position](https://leetcode.com/problems/search-insert-position/)

> 思路

二分查找变形，寻找第一个大于或者等于目标数值的数，没有则返回末尾位置

> 代码

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int low = 0;
		int hight = nums.length - 1;
		while (hight >= low) {
			int mid = low + ((hight - low) >> 1);
			if (nums[mid] >= target) {
				if ((mid == 0) || nums[mid - 1] < target)
					return mid;
				else
					hight = mid - 1;
			} else
				low = mid + 1;
		}
		return nums.length;
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(lgn)

额外使用开始，结束，中间三个int变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Search Insert Position.
Memory Usage: 39.2 MB, less than 100.00% of Java online submissions for Search Insert Position.
