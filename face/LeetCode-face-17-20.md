### LeetCode-face-17-20

> 题目链接

[LeetCode-face-17-20](https://leetcode-cn.com/problems/continuous-median-lcci/)

> 思路

用大小堆保存数据，数据需要先后经过两个堆，然后peek就是中位数相关的数值

> 代码

```java
class MedianFinder {
    private Queue<Integer> A;
    private Queue<Integer> B;
    public MedianFinder() {
        A = new PriorityQueue<>();
        B = new PriorityQueue<>((x, y) -> (y - x));
    }
    public void addNum(int num) {
        if(A.size() != B.size()){
            A.offer(num);
            B.offer(A.poll());
        }else{
            B.offer(num);
            A.offer(B.poll());
        }
    }
    public double findMedian() {
        return A.size() != B.size() ? A.peek() : (A.peek() + B.peek()) / 2.0;
    }
}
```

> 复杂度分析

堆操作，时间复杂度O(logn)

额外使用PriorityQueue辅助，空间复杂度O(n)

> 总结

执行用时：68 ms, 在所有 Java 提交中击败了76.55%的用户

内存消耗：49.8 MB, 在所有 Java 提交中击败了28.76%的用户
