### LeetCode-621-Task-Scheduler

> 题目链接

[LeetCode-621-Task-Scheduler](https://leetcode.com/problems/task-scheduler/)

> 思路

```java
//例子1 {'A','A','A','B','B'},n =2, A <- n -> A  <- n -> A 
//例子2 {'A','A','A','B','B','C','C'},n =1, A <- n -> A  <- n -> A  转为ABABA,插入C为ABCABCA
//例子3 {'A','A','A','B','B','B'},n =1, A <- n -> A  <- n -> A  转为ABABA,插入最后的B，为ABABAB
```
桶排序的思维，先记录每个字母出现的次数，出现最多次数的字母，决定任务完成的至少用时，则有例子1，中间间隔n插入其他任务，如果其他任务插入都不布满，
那么max + （max - 1）* n = (max - 1) * (n + 1) +1为用时。如果布满，见例子2，插入B布满，为ABABA，然后继续在间隔插入剩下的元素，扩大间隔，最常用时为
任务的总长度。排列就只有布满和不布满的情况，但是最多的次数可以有多个字母相同的情况，见例子3，相等的，都可以依次排在后面，则有最长时间
(max - 1) * (n + 1) +count，count为最多的次数的字母个数

> 代码

```java
class Solution {
    public int leastInterval(char[] tasks, int n) {
		int[] task = new int[26];
		for (char a : tasks) {
			task[a - 'A']++;
		}
		int max = task[0];
		int count = 1;
		for (int i = 1; i < 26; i++)
			if (task[i] > max) {
				max = task[i];
				count = 1;
			} else if (task[i] == max)
				count++;
		return Math.max(tasks.length, (max - 1) * (n + 1) + count);
    }
}
```

> 复杂度分析

循环遍历了，时间复杂度O(n)

额外使用了task数组，长度为26，max和count两个基本类型,空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 99.69% of Java online submissions for Task Scheduler.
Memory Usage: 41 MB, less than 7.35% of Java online submissions for Task Scheduler.
