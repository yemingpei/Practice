### LeetCode-232-Implement-Queue-using-Stacks

> 题目链接

[LeetCode-232-Implement-Queue-using-Stacks](https://leetcode.com/problems/implement-queue-using-stacks/submissions/)

> 思路

push的时候用辅助栈，把原来的栈反转
> 代码

```java
class MyQueue {
        Stack<Integer> a, b;
		/** Initialize your data structure here. */
		public MyQueue() {
			a = new Stack<Integer>();
			b = new Stack<Integer>();
		}

		/** Push element x to the back of queue. */
		public void push(int x) {
			if (a.isEmpty())
				a.push(x);
			else {
				while (!a.isEmpty()) {
					b.push(a.pop());
				}
				a.push(x);
				while (!b.isEmpty())
					a.push(b.pop());
			}
		}

		/** Removes the element from in front of queue and returns that element. */
		public int pop() {
			return a.pop();
		}

		/** Get the front element. */
		public int peek() {
			return a.peek();
		}

		/** Returns whether the queue is empty. */
		public boolean empty() {
			return a.isEmpty();
		}
}

```

> 复杂度分析

有倒栈的操作，时间复杂度O(n)

额外使用了辅助栈，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Implement Queue using Stacks.
Memory Usage: 37.3 MB, less than 6.25% of Java online submissions for Implement Queue using Stacks.
