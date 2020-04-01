### LeetCode-80-Remove Duplicates from Sorted Array II

> 题目链接

[LeetCode-80-Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

> 思路

从左边开始遍历，遇到count没有2的数就往记录指针的位置移动，超过2就跳过

> 代码

```java
class Solution {
    public int removeDuplicates(int[] nums) {
		int indicator = 1;
		int count = 1;
		for (int i = 1; i < nums.length; i++) {
			if (nums[i] > nums[i - 1]) {
				count = 1;
				nums[indicator++] = nums[i];
			} else if (count < 2) {
				nums[indicator++] = nums[i];
				count++;
			}
		}
		return indicator;
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，时间复杂度O(n)

额外使用了两个int类型，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Remove Duplicates from Sorted Array II.
Memory Usage: 40 MB, less than 5.26% of Java online submissions for Remove Duplicates from Sorted Array II.
