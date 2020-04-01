### LeetCode-670-Maximum-Swap

> 题目链接

[LeetCode-670-Maximum-Swap](https://leetcode.com/problems/maximum-swap/)

> 思路

先看几个例子

```java
//例子1：9876654321 ，顺序从大到小，无须更换位置
//例子2：9875561234 ，从左边开始遍历，找出98755，6的时候就变大，所以第一个5就是分割的位置
//例子3：6542221399 ，从左边开始遍历，找出6542221，3的时候就变大，1就是分割的位置，因为后面的最大数字是9，从左边开始替换第一个比最大数字大的位置
```

综上所述，先找到左边的分割位置，然后从右边往分割位置遍历，找到第一个最大的数，从左开始对比，替换第一个比最大的数小的数字。

> 代码

```java
class Solution {
    public int maximumSwap(int num) {
        if (num < 12) return num;
		char[] numString = Integer.toString(num).toCharArray();
		int flag = -1;
		for (int i = 0; i < numString.length - 1; i++) {
			if (numString[i] < numString[i + 1]) {
				flag = i;
				break;
			}
		}
		if (flag == -1) return num;
		int end = numString.length - 1;
		char endNum = numString[end];
		for (int i = end; i > flag; i--) {
			if (numString[i] > endNum) {
				end = i;
				endNum = numString[i];
			}
		}
		for (int i = 0; i <= flag; i++) {
			if (endNum > numString[i]) {
				numString[end] = numString[i];
				numString[i] = endNum;
				break;
			}
		}
		return Integer.valueOf(new String(numString));
    }
}
```

> 复杂度分析

最坏情况循环遍历不超过两遍数组，时间复杂度O(n)

额外使用了char[]数组,大小为n，还有额外的几个int变量，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Maximum Swap.
Memory Usage: 36.5 MB, less than 25.00% of Java online submissions for Maximum Swap.
