### LeetCode-933-Number-of-Recent-Calls

> 题目链接

[LeetCode-933-Number-of-Recent-Calls](https://leetcode.com/problems/number-of-recent-calls/)

> 思路

可以用队列，先进先出来解，这个不多做介绍
因为这个肯定是个递增数列，用二分查找可以减少查询的次数，更快找到t -3000的临界点

> 代码

```java
class RecentCounter {
    private int[] number;
	private int position = 0;
    int left = 0;
    public RecentCounter() {
        number = new int[10000];
    }
    
    public int ping(int t) {
        number[position] = t;
		int min = t - 3000;
		int right = position;
		while (left <= right) {
			int mid = (left + right) / 2;
			if (number[mid] < min)
				left = mid + 1;
			else if (number[mid] == min) {
				left = mid;
				break;
			} else
				right = mid - 1;
		}
		position++;
		return position - left;
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(logn)

用了一个int数组，空间复杂度O(n)

> 总结

Runtime: 18 ms, faster than 97.32% of Java online submissions for Number of Recent Calls.
Memory Usage: 48.3 MB, less than 100.00% of Java online submissions for Number of Recent Calls.
