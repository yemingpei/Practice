### LeetCode-150-Evaluate-Reverse-Polish-Notation

> 题目链接

[LeetCode-150-Evaluate-Reverse-Polish-Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

> 思路

利用递归，不断输出算式的对应的数字达到计算等式的效果

> 代码

```java
class Solution {
    int position;
	public int evalRPN(String[] tokens) {
		position = tokens.length - 1;
		return eval(tokens);
	}

	public int eval(String[] tokens) {
		if (tokens[position].equals("+")) {
			position--;
			int a = eval(tokens);
			position--;
			int b = eval(tokens);
			return a + b;
		} else if (tokens[position].equals("/")) {
			position--;
			int a = eval(tokens);
			position--;
			int b = eval(tokens);
			return b / a;
		} else if (tokens[position].equals("-")) {
			position--;
			int a = eval(tokens);
			position--;
			int b = eval(tokens);
			return b - a;
		} else if (tokens[position].equals("*")) {
			position--;
			int a = eval(tokens);
			position--;
			int b = eval(tokens);
			return a * b;
		} else {
			return new Integer(tokens[position]);
		}
	}
}
```

> 复杂度分析

递归遍历了一遍数组，时间复杂度O(n)

额外使用一个int辅助，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Evaluate Reverse Polish Notation.
Memory Usage: 40.2 MB, less than 6.00% of Java online submissions for Evaluate Reverse Polish Notation.
