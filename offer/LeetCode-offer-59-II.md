### LeetCode-offer-59-II

> 题目链接

[LeetCode-offer-59-II](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/)

> 思路

比较数字的大小，如果比队列头小，则继续排队，否则替换掉比它小的全部数字

> 代码

```java
class MaxQueue {
    LinkedList<Integer> queue;
    int maxVal = 0;

    public MaxQueue() {
        queue = new LinkedList<>();
    }

    public int max_value() {
        if (queue.size() == 0) return -1;
        else return maxVal;
    }

    public void push_back(int value) {
        queue.add(value);
        maxVal = Math.max(value, maxVal);
    }

    public int pop_front() {
        if (queue.size() == 0) return -1;
        else {
            int ans = queue.removeFirst();
            if (ans == maxVal) {
                maxVal = -1;
                for (int i = 0; i < queue.size(); i++) {
                    maxVal = Math.max(maxVal, queue.get(i));
                }
            }
            return ans;
        }
    }
}
```

> 复杂度分析

遍历队列，时间复杂度O(n)

额外使用队列，空间复杂度O(n)

> 总结

执行用时：37 ms, 在所有 Java 提交中击败了98.79%的用户

内存消耗：46.9 MB, 在所有 Java 提交中击败了5.86%的用户
