### LeetCode-face-03-03

> 题目链接

[LeetCode-face-03-03](https://leetcode-cn.com/problems/stack-of-plates-lcci/)

> 思路

用数组实现栈，快速检索方便操作，用LinkedList方便修改和删除

> 代码

```java
class StackOfPlates {
    private LinkedList<LinkedList<Integer>> list = new LinkedList<>();
    private int cap;
    public StackOfPlates(int cap) {
        this.cap = cap;
    }
    
    public void push(int val) {
        if (cap <= 0) return;
        if(!list.isEmpty() && list.get(list.size() - 1).size() < cap){
            list.get(list.size() - 1).add(val);
        }else{
            LinkedList<Integer> number = new LinkedList<>();
            number.add(val);
            list.add(number);
        }
    }
    
    public int pop() {
        if(list.isEmpty()) return -1;
        int number = list.get(list.size() - 1).remove(list.get(list.size() - 1).size() - 1);
        if(list.get(list.size() - 1).isEmpty()) list.remove(list.size() - 1);
        return number;
    }
    
    public int popAt(int index) {
        if(index < 0 || index >= list.size()) return -1;
        int number = list.get(index).remove(list.get(index).size() - 1);
        if(list.get(index).isEmpty()) list.remove(index);
        return number;
    }
}
```

> 复杂度分析

用数组的方式模拟stack，时间复杂度O(1)

额外使用list，空间复杂度O(n * cap)

> 总结

执行用时：13 ms, 在所有 Java 提交中击败了92.74%的用户

内存消耗：46.1 MB, 在所有 Java 提交中击败了55.53%的用户
