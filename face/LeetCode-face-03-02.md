### LeetCode-face-03-02

> 题目链接

[LeetCode-face-03-02](https://leetcode-cn.com/problems/min-stack-lcci/)

> 思路

用链表实现栈，同时保存目前栈内的最小值

> 代码

```java
class MinStack {
    private Node head;
    public MinStack() {

    }
    
    public void push(int x) {
        int min = head == null? x : Math.min(x, head.min);
        Node node = new Node(min, x);
        node.next = head;
        head = node;
    }
    
    public void pop() {
        if(head != null) head = head.next;
    }
    
    public int top() {
        return head.val;
    }
    
    public int getMin() {
        return head.min;
    }
}

class Node{
    int min;
    int val;
    Node next;
    public Node(int min, int val){
        this.min = min;
        this.val = val;
    }
}
```

> 复杂度分析

用链表的方式模拟stack，时间复杂度O(1)

额外使用链表，空间复杂度O(n)

> 总结

执行用时：20 ms, 在所有 Java 提交中击败了99.83%的用户

内存消耗：40.1 MB, 在所有 Java 提交中击败了62.25%的用户
