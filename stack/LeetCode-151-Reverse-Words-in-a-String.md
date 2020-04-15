### LeetCode-151-Reverse-Words-in-a-String

> 题目链接

[LeetCode-151-Reverse-Words-in-a-String](https://leetcode.com/problems/reverse-words-in-a-string/)

> 思路

string转化为char数组，从后面开始往前面遍历，以空格为界，先找第一个右边不为空格的字符，然后找左边为空的字符，拼接到目标字串的上

> 代码

```java
class Solution {
    public String reverseWords(String s) {
		char[] text = s.toCharArray();
		StringBuilder result = new StringBuilder();
		int position = text.length - 1;
		while (position >= 0) {
			position = takeString(position, text, result);
		}
		return result.toString();
	}

	public int takeString(int position, char[] text, StringBuilder result) {
		int end = position;
		while (end >= 0 && text[end] == ' ') {
			end--;
		}
        if (end < 0) return end;
		int start = end;
		while (start >= 0 && text[start] != ' ') {
			start--;
		}
		if (result.length() > 0) {
			result.append(' ');
		}
		for (int i = start + 1; i <= end; i++) {
			result.append(text[i]);
		}
		return start;
	}
}
```

> 复杂度分析

遍历了一遍String的长度的char数组，时间复杂度O(n)

额外使用了char数组，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.71% of Java online submissions for Reverse Words in a String.
Memory Usage: 39.7 MB, less than 25.80% of Java online submissions for Reverse Words in a String.
