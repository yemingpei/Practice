### LeetCode-32-Longest-Valid-Parentheses

> 题目链接

[LeetCode-32-Longest-Valid-Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)

> 思路

先举几个例子
```java
//例子1："(())" 数量相等，且有效
//例子2："))((" 数量相等，但无效
//例子3："(()" 数量不相等，(多
//例子4："())" 数量不相等，)多
```
例子1相等，有效，就用"("的个数 * 2,就可以得出有效长度。
例子2要转化为无效，所以当")" > "("就重置他们的计数。
再看看例子4，")" 和 "("的个数相等就计算，符合例子1。
最后看看例子3，有了上面的判断就判断不出来了，所以倒回来再查一下，即上面的判断相反，")" < "("重置

> 代码

```java
class Solution {
    public int longestValidParentheses(String s) {
        int res = 0, left = 0, leftPosition = 0, right = 0, size = s.length();
		for (int i = 0; i < size; ++i) {
			if (s.charAt(i) == '(')
				++left;
			else
				++right;
			if (left == right) {
				leftPosition = i;
				res = Math.max(res, 2 * right);
			} else if (right > left)
				left = right = 0;
		}
		left = right = 0;
		for (int i = size - 1; i >= leftPosition; --i) {
			if (s.charAt(i) == '(')
				++left;
			else
				++right;
			if (left == right)
				res = Math.max(res, 2 * left);
			else if (left > right)
				left = right = 0;
		}
		return res;
    }
}
```

> 复杂度分析

顺序遍历了一遍字符串，然后再到回来遍历到上一次有效相等的位置，最坏应该是遍历了2n，时间复杂度O(n)

额外使用了5个int变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Longest Valid Parentheses.
Memory Usage: 38 MB, less than 60.78% of Java online submissions for Longest Valid Parentheses.
