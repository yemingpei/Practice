### LeetCode-15-3Sum

> 题目链接

[LeetCode-15-3Sum](https://leetcode.com/problems/3sum/)

> 思路

先看几个例子

```java
//例子1：[-1,2,3,4,5,6]
//例子2：[-5，-4，-3，-2，-1,6]
//例子3：[-3,-2,-1,4,5,6]
```

先确定最左边的一个数a，然后从右边找两数之和为0-a;同理也可以先确定最右边的一个数b，然后从右边找两数之和为0-b。左边寻找负数边界，右边寻找正数边界，这样就可以确保最外层的循环不超过n/2,到达省时的效果。

上述例子1，应该确定左边的，从右边去找两数之和，例子2应该确定右边的，从左边去找两数之和，例子3就是最坏的情况，需要执行n/2次


> 代码

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
       List<List<Integer>> result = new ArrayList<List<Integer>>();
		if (nums.length > 2) {
			Arrays.sort(nums);
			int criticalLeft = -1;
			int criticalRight = -1;
			int end = nums.length - 1;
			int start = 0;
			while (end >= start) {
				if (nums[start] >= 0) {
					criticalLeft = start;
					break;
				}
				if (nums[end] <= 0) {
					criticalRight = end;
					break;
				}
				start++;
				end--;
			}
            if (criticalLeft == -1 && criticalRight == -1)criticalLeft = start - 1;

			if (criticalLeft != -1) {
				for (int i = 0; i <= criticalLeft; i++) {
					if (i != 0 && nums[i] == nums[i - 1])
						continue;
					findTwoSumResult(nums, result, i + 1, nums.length - 1,
							0 - nums[i], nums[i]);
				}
			} else {
				for (int i = nums.length - 1; i >= criticalRight; i--) {
					if (i != nums.length - 1 && nums[i] == nums[i + 1])
						continue;
					findTwoSumResult(nums, result, 0, i - 1, 0 - nums[i],
							nums[i]);
				}
			}
		}
		return result;
    }
    
    public void findTwoSumResult(int[] nums, List<List<Integer>> result,
			int flagLeft, int flagRight, int sum, int number) {
		while (flagRight > flagLeft) {
			if (nums[flagLeft] + nums[flagRight] == sum) {
				result.add(Arrays.asList(number, nums[flagLeft], (nums[flagRight])));
				while (flagRight > flagLeft
						&& nums[flagLeft] == nums[flagLeft + 1]) {
					flagLeft++;
				}
				while (flagRight > flagLeft
						&& nums[flagRight] == nums[flagRight - 1]) {
					flagRight--;
				}
				flagLeft++;
				flagRight--;
			} else if (nums[flagLeft] + nums[flagRight] > sum) {
				flagRight--;
			} else {
				flagLeft++;
			}
		}
	}
}
```

> 复杂度分析

排序的时间复杂度是O(nlogn)，计算criticalLeft和criticalRight，用时应该是O(n)，findTwoSumResult寻找两数之和时间复杂度应该是O(n)，则最外层的for循环应该是(n/2)*n，则整体复杂度应该为nlogn+n^2，应该为O(n^2)

额外使用了左右位置的标识，空间复杂度O(1)

> 总结

Runtime: 15 ms Memory Usage: 43.7 MB,三数之和调用两数之和，同理，四数之和，也是如此
