### LeetCode-220-Contains-Duplicate-III

> 题目链接

[LeetCode-220-Contains-Duplicate-III](https://leetcode.com/problems/contains-duplicate-iii/)

> 思路

当t < 0直接返回false，当t == 0，寻找窗口为k的范围内有没有相同的数字，当t>1的时候，用t作为桶的大小，来分发数字，如果同一个桶存在两个数字或者相邻的桶
存在差值的相对值<=k，直接返回false，同时需要维护map的大小为k

> 代码

```java
class Solution {
    private long getID(long x, long w) {
		return x < 0 ? (x + 1) / w - 1 : x / w;
	}

	public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
        if (t < 0) return false;
		if (t == 0) {
			Map<Integer, Boolean> map = new HashMap();
			for (int i = 0; i < nums.length; ++i) {
				if (i > k) map.put(nums[i - k], false);
				if (map.getOrDefault(nums[i],false)) return true;
				map.put(nums[i], true);
			}
            return false;
		}
		Map<Long, Long> bucket = new HashMap();
		long difference = (long) t;
		for (int i = 0; i < nums.length; ++i) {
			if (i > k) bucket.remove(getID(nums[i - k -1], difference));
			long position = getID(nums[i], difference);
			if (bucket.containsKey(position)) return true;
			if (bucket.containsKey(position - 1) && Math.abs(nums[i] - bucket.get(position - 1)) <= difference)
				return true;
			if (bucket.containsKey(position + 1) && Math.abs(nums[i] - bucket.get(position + 1)) <= difference)
				return true;
			bucket.put(position, (long) nums[i]);
		}
		return false;
	}
}
```

> 复杂度分析

仅遍历一遍数组，时间复杂度O(n)

额外使用了HashMap，大小为k，空间复杂度O(k)

> 总结

Runtime: 4 ms, faster than 97.81% of Java online submissions for Contains Duplicate III.

Memory Usage: 39.9 MB, less than 6.82% of Java online submissions for Contains Duplicate III.
