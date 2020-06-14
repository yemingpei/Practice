### LeetCode-44-Wildcard-Matching

> 题目链接

[LeetCode-44-Wildcard-Matching](https://leetcode.com/problems/wildcard-matching/)

> 思路

用暴力法一一比较，如果是'?'或者相等，则指针一起移动，如果是'*'只移动p的指针，还需要处理临界点

> 代码

```java
class Solution {
    public boolean isMatch(String s, String p) {
	if (s.equals(p)) return true;
	int i = 0, j = 0;
	int starti = -1, startj = -1;
	while (i < s.length()) {
		if (j < p.length() && (p.charAt(j) == '?' || p.charAt(j) == s.charAt(i))) {
			i++;
			j++;
		} else if (j < p.length() && p.charAt(j) == '*') {
			starti = i;
			startj = j;
			j++;
		} else if (startj != -1) {
			j = startj + 1;
			i = starti + 1;
			starti++;
		} else return false;
	}
	while (j < p.length() && p.charAt(j) == '*')
		j++;
	return j == p.length();
    }
}
```

> 复杂度分析

双循环遍历对应的s和p，时间复杂度O(n ^ 2)

额外使用4个辅助int来记录移动的位置，空间复杂度O(1)

> 总结

Runtime: 5 ms, faster than 84.38% of Java online submissions for Wildcard Matching.

Memory Usage: 41.5 MB, less than 24.42% of Java online submissions for Wildcard Matching.
