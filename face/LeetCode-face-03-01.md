### LeetCode-face-03-01

> 题目链接

[LeetCode-face-03-01](https://leetcode-cn.com/problems/three-in-one-lcci/)

> 思路

用数组初始化三个栈，每个的第一个位置保存指针的位置，以此判断是否满和空，便于出栈

> 代码

```java
class TripleInOne {
    private int[] number;
    private int size;
    private int eachStackSize;
    public TripleInOne(int stackSize) {
        number = new int[stackSize * 3 + 3];
        size = stackSize + 1;
        number[size] = size;
        number[2 * size] = 2 * size;
        eachStackSize = stackSize;
    }
    
    public void push(int stackNum, int value) {
        int flag = stackNum * size;
        if(number[flag] - flag < eachStackSize) number[++number[flag]] = value;
    }
    
    public int pop(int stackNum) {
        int flag = stackNum * size;
        if(number[flag] == flag) return -1;
        return number[number[flag]--];
    }
    
    public int peek(int stackNum) {
        int flag = stackNum * size;
        if(number[flag] == flag) return -1;
        return number[number[flag]];
    }
    
    public boolean isEmpty(int stackNum) {
        int flag = stackNum * size;
        return number[flag] == flag;
    }
}
```

> 复杂度分析

用数组模拟指针的方式模拟stack，时间复杂度O(1)

一个数组保存三个stack大小的数组，空间复杂度O(n)

> 总结

执行用时：12 ms, 在所有 Java 提交中击败了91.53%的用户

内存消耗：47.3 MB, 在所有 Java 提交中击败了81.88%的用户
