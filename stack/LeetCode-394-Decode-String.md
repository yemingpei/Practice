### LeetCode-394-Decode-String

> 题目链接

[LeetCode-394-Decode-String](https://leetcode.com/problems/decode-string/)

> 思路

String栈保存字符串，Integer栈保存数字，'['直接进站，遇到']'就开始复制字符，然后再建栈。最后遍历栈，倒序输出。

> 代码

```java
class Solution {
    public String decodeString(String s) {
        Stack<String> stack = new Stack<String>();
	Stack<Integer> numStack = new Stack<Integer>();
	StringBuilder text = new StringBuilder();
	for (int i = 0; i < s.length(); i++) {
		char c = s.charAt(i);
		if (c == ']') {
			StringBuilder temp = new StringBuilder();
			String a = stack.pop();
			while (!a.equals("[")) {
				text.insert(0, a);
				a = stack.pop();
			}
			int size = numStack.pop();
			for (int j = 0; j < size; j++) {
				temp.append(text);
			}
			stack.push(temp.toString());
			text = new StringBuilder();
		} else if (c >= '0' && c <= '9') {
			int num = 0;
			while (s.charAt(i) >= '0' && s.charAt(i) <= '9') {
				num = num * 10 + s.charAt(i) - '0';
				i++;
			}
			numStack.push(num);
			if (text.length() > 0)
				stack.push(text.toString());
			stack.push("[");
			text = new StringBuilder();
		} else {
			text.append(c);
		}
	}
	while (!stack.isEmpty()) {
		text.insert(0, stack.pop());
	}
	return text.toString();
    }
}
```

> 复杂度分析

循环遍历了一遍字符串长度，时间复杂度O(n)

额外使用了栈辅助，来保存数据，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Decode String.
Memory Usage: 37.7 MB, less than 5.68% of Java online submissions for Decode String.
