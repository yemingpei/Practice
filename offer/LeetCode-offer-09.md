### LeetCode-offer-09

> 题目链接

[LeetCode-offer-09](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

> 思路

进栈保存在stack，出栈的时候先移动到stack2，然后判断两个栈是否都是空来判断是否有数据，节省操作

> 代码

```java
class CQueue {
    private Stack<Integer> stack;
    private Stack<Integer> stack2;
    public CQueue() {
        stack = new Stack<>();
        stack2 = new Stack<>();
    }
    public void appendTail(int value) {
        stack.push(value);
    }
    public int deleteHead() {
        if(!stack2.isEmpty()) return stack2.pop();
        if(!stack.isEmpty()){
            while(!stack.isEmpty()){
                stack2.push(stack.pop());
            }
            return stack2.pop();
        }
        return -1;
    }
}
```

> 复杂度分析

进栈出栈操作，时间复杂度O(n)

使用两个栈，空间复杂度O(n)

> 总结

执行用时：57 ms, 在所有 Java 提交中击败了73.84%的用户

内存消耗：46.3 MB, 在所有 Java 提交中击败了93.41%的用户

