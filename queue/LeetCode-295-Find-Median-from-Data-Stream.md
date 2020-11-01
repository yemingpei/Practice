### LeetCode-295-Find-Median-from-Data-Stream

> 题目链接

[LeetCode-295-Find-Median-from-Data-Stream](https://leetcode.com/problems/find-median-from-data-stream/)

> 思路

大小堆，来表示中位数前面部分和后面部分，插入数据的时候要调整两个堆的大小

> 代码

```java
class MedianFinder {
    PriorityQueue<Integer> maxHeap ;
    PriorityQueue<Integer> minHeap ;
    public MedianFinder() {
      maxHeap =new PriorityQueue<Integer>(Collections.reverseOrder());
      minHeap =new PriorityQueue<Integer>();
    }
    
    public void addNum(int num) {
        double median = this.findMedian();
        if(num>median){
            minHeap.offer(num);
        }else{
            maxHeap.offer(num);
        }
        if(minHeap.size()-maxHeap.size() > 1){
            maxHeap.offer(minHeap.poll());
        }
         if(maxHeap.size()-minHeap.size() > 1){
            minHeap.offer(maxHeap.poll());
        }
    }
    
    public double findMedian() {
        if(minHeap.size()==0 && maxHeap.size()==0)
            return 0.0;
        if(minHeap.size()==0 && maxHeap.size()>0)
            return maxHeap.peek();
        if(minHeap.size()>maxHeap.size())
            return minHeap.peek();
        else if(maxHeap.size()>minHeap.size())
            return maxHeap.peek();
        else 
            return (double)(maxHeap.peek()+minHeap.peek())/2.0;
    }
}

```

> 复杂度分析

插入和移除的操作都是logn，其他操作时间复杂度O(logn)

额外使用队列表示大小堆，空间复杂度O(n)

> 总结

Runtime: 43 ms, faster than 96.14% of Java online submissions for Find Median from Data Stream.

Memory Usage: 50.6 MB, less than 10.25% of Java online submissions for Find Median from Data Stream.
