### LeetCode-225-Implement-Stack-using-Queues

> 题目链接

[LeetCode-225-Implement-Stack-using-Queues](https://leetcode.com/problems/implement-stack-using-queues/)

> 思路

用队列实现栈，入栈的时候，先记录队列有多少个数，然后数字入队列，队列原来的数字重新入队列

> 代码

```java
class MyStack {
    
    Queue<Integer> queue;
    
    public MyStack() {
        queue = new LinkedList<>();
    }
    
    public void push(int x) {
        int n = queue.size();
        queue.offer(x);
        for(int i = 0; i < n; i++){
            queue.offer(queue.poll());
        }
    }
    
    public int pop() {
        return queue.poll();
    }
    
    public int top() {
        return queue.peek();
    }
    
    public boolean empty() {
        return queue.isEmpty();
    }
}
```

> 复杂度分析

入栈的复杂度O(n)，其他操作时间复杂度O(1)

额外使用队列来辅助，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Implement Stack using Queues.

Memory Usage: 36.8 MB, less than 17.27% of Java online submissions for Implement Stack using Queues.
