### LeetCode-155-Min-Stack

> 题目链接

[LeetCode-155-Min-Stack](https://leetcodeLeetCode-155-Min-Stack.com/problems/min-stack/)

> 思路

stack保存于最小值的差值，便于还原原来的值，因为用int类型会溢出，所以使用了long，如果题目给出输入值的范围，则可以使用int，这样就不需要使用额外的空间

> 代码

```java
class MinStack {
        private int min;
		private Stack<Long> stack = new Stack<Long>();
		public MinStack() {

		}

		public void push(int x) {
			if (stack.isEmpty()) {
				min = x;
				stack.push((long) 0);
			} else {
				long a = (long) x - min;
				stack.push(a);
				if (a < 0)
					min = x;
			}
		}

		public void pop() {
			Long a = stack.pop();
			if (a < 0)
				min = (int)(min - a);
		}

		public int top() {
			long a = stack.peek();
			if (a < 0)
				return min;
			else
				return (int) (stack.peek() + min);
		}

		public int getMin() {
			return min;
		}
}
```

> 复杂度分析

查询时间都是1，时间复杂度O(1)

额外使用了一个min，和普通栈没有什么区别,空间复杂度O(1)

> 总结

Runtime: 5 ms, faster than 68.93% of Java online submissions for Min Stack.
Memory Usage: 41.1 MB, less than 18.12% of Java online submissions for Min Stack.
