### LeetCode-offer-30

> 题目链接

[LeetCode-offer-30](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

> 思路

每次从表头插入节点，来模拟stack先进后出

> 代码

```java
class MinStack {
    private Node head; 
    public MinStack() {
    }
    
    public void push(int x) {
        if(head == null){
            head = new Node(x, x, null);
        }else{
            head = new Node(x, Math.min(x, head.min), head);
        }
    }
    
    public void pop() {
        head = head.next;
    }
    
    public int top() {
        return head.val;
    }
    
    public int min() {
        return head.min;
    }
}

public class Node{
    int val;
    int min;
    Node next;
    public Node(int val, int min, Node next){
        this.val = val;
        this.min = min;
        this.next = next;
    }
}
```

> 复杂度分析

函数操作为常数级别，时间复杂度O(1)

额外使用链表保存数据，空间复杂度O(n)

> 总结

执行用时：21 ms, 在所有 Java 提交中击败了98.97%的用户

内存消耗：40.1 MB, 在所有 Java 提交中击败了86.80%的用户
