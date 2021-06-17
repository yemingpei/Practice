### LeetCode-face-03-04

> 题目链接

[LeetCode-face-03-04](https://leetcode-cn.com/problems/implement-queue-using-stacks-lcci/)

> 思路

用两个栈，来更换顺序，如果stackOut为空，则从stackIn转入

> 代码

```java
class MyQueue {
    private Stack<Integer> stackIn;
    private Stack<Integer> stackOut;
    public MyQueue() {
        stackIn = new Stack<>();
        stackOut = new Stack<>();
    }
	
    public void push(int x) {
        stackIn.push(x);
    }
	
    public int pop() {
        if(stackOut.isEmpty() && stackIn.isEmpty()) return -1;
        if(stackOut.isEmpty()){
            while(!stackIn.isEmpty())
                stackOut.push(stackIn.pop());
        }
        return stackOut.pop();
    }
	
    public int peek() {
        if(stackOut.isEmpty() && stackIn.isEmpty()) return -1;
        if(stackOut.isEmpty()){
            while(!stackIn.isEmpty())
                stackOut.push(stackIn.pop());
        }
        return stackOut.peek();
    }
	
    public boolean empty() {
        return stackOut.isEmpty() && stackIn.isEmpty();
    }
}
```

> 复杂度分析

每个元素会经过两次移动，push 时间复杂度O(1) peek和pop最坏时间复杂度O(n)

额外使用stack，空间复杂度O(n)

> 总结

执行用时：16 ms, 在所有 Java 提交中击败了83.89%的用户

内存消耗：36 MB, 在所有 Java 提交中击败了84.82%的用户
