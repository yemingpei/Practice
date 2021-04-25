### LeetCode-offer-41

> 题目链接

[LeetCode-offer-41](https://leetcode-cn.com/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)

> 思路

利用小顶堆，大顶堆的特性，维持两个堆的数量，然后取堆顶作为中位数

> 代码

```java
class MedianFinder {
    Queue<Integer> A, B;
    public MedianFinder() {
        A = new PriorityQueue<>();
        B = new PriorityQueue<>((x, y) -> (y - x));
    }
    public void addNum(int num) {
        if(A.size() != B.size()) {
            A.add(num);
            B.add(A.poll());
        } else {
            B.add(num);
            A.add(B.poll());
        }
    }
    public double findMedian() {
        return A.size() != B.size() ? A.peek() : (A.peek() + B.peek()) / 2.0;
    }
}
```

> 复杂度分析

双堆，addNum时间复杂度O(nlogn)，findMedian时间复杂度O(1)

额外使用最小堆，最大堆，空间复杂度O(n)

> 总结

执行用时：82 ms, 在所有 Java 提交中击败了71.07%的用户

内存消耗：49.6 MB, 在所有 Java 提交中击败了61.90%的用户
