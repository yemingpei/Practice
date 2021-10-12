### LeetCode-480-sliding-window-median

> 题目链接

[LeetCode-480-sliding-window-median](https://leetcode-cn.com/problems/sliding-window-median/)

> 思路

使用大小堆，分别记录数据，peek就是中位数相关的值，注意添加或者移除后，要平衡两个queue的数量

> 代码

```java
class Solution {
    public double[] medianSlidingWindow(int[] nums, int k) {
        DualHeap heap = new DualHeap(k);
        for (int i=0; i < k; i++) {
            heap.add(nums[i]);
        }
        double[] res = new double[nums.length - k + 1];
        res[0] = heap.getMid();
        for (int i = k ; i< nums.length; i++) {
            heap.add(nums[i]);
            heap.delete(nums[i - k]);
            res[i - k + 1] = heap.getMid();
        }
        return res;
  }

  class DualHeap {
    PriorityQueue<Integer> small;
    PriorityQueue<Integer> large;
    int k;
    int smallCnt;
    int largeCnt;
    Map<Integer, Integer> deleted;

    public DualHeap(int k) {
        this.k = k;
        small = new PriorityQueue<>(Comparator.reverseOrder());
        large = new PriorityQueue<>();
        deleted = new HashMap<>();
        smallCnt = 0;
        largeCnt = 0;
    }

    double getMid() {
        if (k % 2 == 0) {
        return (small.peek()*1.0 + large.peek()) / 2.0;
        } else {
        return small.peek();
        }
    }

    private void prune(PriorityQueue<Integer> queue) {
        while (!queue.isEmpty() && deleted.containsKey(queue.peek())) {
            int curr = queue.poll();
            deleted.put(curr, deleted.get(curr) - 1);
            if (deleted.get(curr) == 0) {
                deleted.remove(curr);
            }
        }
    }

    private void balance() {
        if (smallCnt > largeCnt + 1) {
            smallCnt--;
            largeCnt++;
            large.add(small.poll());
            prune(small);
        } else if (smallCnt < largeCnt) {
            smallCnt++;
            largeCnt--;
            small.add(large.poll());
            prune(large);
        }
    }

    void add(int x) {
        if (small.isEmpty() || x <= small.peek()) {
            small.add(x);
            smallCnt++;
        } else {
            large.add(x);
            largeCnt++;
        }
        balance();
    }

    void delete(int x) {
        deleted.put(x, deleted.getOrDefault(x, 0) + 1);
        if (x <= small.peek()) {
            smallCnt--;
            prune(small);
        } else {
            largeCnt--;
            prune(large);
        }
        balance();
    }
  }
}
```

> 复杂度分析

操作双队列，时间复杂度O(nlogn)

额外使用queue辅助，空间复杂度O(n)

> 总结

执行用时：15 ms, 在所有 Java 提交中击败了87.48%的用户
内存消耗：40.4 MB, 在所有 Java 提交中击败了50.79%的用户

