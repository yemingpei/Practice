### LeetCode-641-Design-Circular-Deque

> 题目链接

[LeetCode-641-Design-Circular-Deque](https://leetcode.com/problems/design-circular-deque/)

> 思路

用数组来保存数据，前后指针，判空是start == end，满的判断条件是 (end + 1) % size == start，所以数组大小是k+1

> 代码

```java
        private int[] number;
	private int start = 0;
	private int end = 0;
	private int size;
    public MyCircularDeque(int k) {
        size = k + 1;
	number = new int[size];
    }
    
    public boolean insertFront(int value) {
       if (isFull())
       		return false;
	start = (start - 1 + size) % size;
	number[start] = value;
	return true; 
    }
    
    public boolean insertLast(int value) {
        if (isFull())
			return false;
	number[end] = value;
	end = (end + 1) % size;
	return true;
    }
    
    public boolean deleteFront() {
        if (isEmpty())
		return false;
	start = (start + 1) % size;
	return true;
    }
    
    public boolean deleteLast() {
       if (isEmpty())
		return false;
	end = (end - 1 + size) % size;
	return true; 
    }
    
    public int getFront() {
        if (isEmpty())
		return -1;
	else
		return number[start];
    }
    
    public int getRear() {
        if (isEmpty())
		return -1;
	else
		return number[(end - 1 + size) % size];
    }
    
    public boolean isEmpty() {
        return start == end;
    }
    
    public boolean isFull() {
        return (end + 1) % size == start;
    }
```

> 复杂度分析

查询，插入，删除都是1，时间复杂度O(1)

额外使用int数组，空间复杂度O(n)

> 总结

Runtime: 4 ms, faster than 99.63% of Java online submissions for Design Circular Deque.
Memory Usage: 39.9 MB, less than 50.00% of Java online submissions for Design Circular Deque.
