### LeetCode-face-03-05

> 题目链接

[LeetCode-face-03-05](https://leetcode-cn.com/problems/sort-of-stacks-lcci/)

> 思路

保证stack1是大到小，每次要出栈的时候都需要往stack2倒一次

> 代码

```java
class SortedStack {
    private Stack<Integer> stk1;
    private Stack<Integer> stk2;
    public SortedStack() {
        stk1 = new Stack<>();
        stk2 = new Stack<>();
    }
    
    public void push(int val) {
        while(!stk1.isEmpty() && stk1.peek() > val){
            stk2.push(stk1.pop());
        }

        while(!stk2.isEmpty() && stk2.peek() < val){
            stk1.push(stk2.pop());
        }
        stk1.push(val);
    }
    
    public void pop() {
        peek();
        if(stk2.isEmpty()) return;
        stk2.pop();
    }
    
    public int peek() {
        while(!stk1.isEmpty()){
            stk2.push(stk1.pop());
        }
        if(stk2.isEmpty()) return -1;
        return stk2.peek();
    }
    
    public boolean isEmpty() {
        return stk1.isEmpty() && stk2.isEmpty();
    }
}
```

> 复杂度分析

每个元素会经过多次移动，时间复杂度O(n) 

额外使用stack，空间复杂度O(n)

> 总结

执行用时：22 ms, 在所有 Java 提交中击败了93.30%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了86.06%的用户
