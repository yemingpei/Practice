### LeetCode-622-Design-Circular-Queue

> 题目链接

[LeetCode-622-Design-Circular-Queue](https://leetcode.com/problems/design-circular-queue/)

> 思路

用数组来保存数据，前后指针，判空是start == end，满的判断条件是 (end + 1) % size == start，所以数组大小是k+1

> 代码

```java
class MyCircularQueue {
    private int[] number;
    private int start = 0;
	  private int end = 0;
	  private int size;
    public MyCircularQueue(int k) {
        size = k + 1;
		number = new int[size];
    }
    
    public boolean enQueue(int value) {
        if (isFull()) return false;
        number[end] = value;
        end = (end + 1) % size;
        return true;
    }
    
    public boolean deQueue() {
        if (isEmpty()) return false;
        start = (start + 1) % size;
        return true;
    }
    
    public int Front() {
        if (isEmpty()) return -1;
		    else return number[start];
    }
    
    public int Rear() {
        if (isEmpty()) return -1;
		    else return number[(end - 1 + size) % size];
    }
    
    public boolean isEmpty() {
        return start == end;
    }
    
    public boolean isFull() {
        return (end + 1) % size == start;
    }
}
```

> 复杂度分析

查询，插入，删除都是1，时间复杂度O(1)

额外使用int数组，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Design Circular Queue.
Memory Usage: 40 MB, less than 10.72% of Java online submissions for Design Circular Queue.
