### LeetCode-offer-59-I

> 题目链接

[LeetCode-offer-598-I](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)

> 思路

比较数字的大小，如果比队列头小，则继续排队，否则替换掉比它小的全部数字

> 代码

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if (nums == null || nums.length == 0) {
            return new int[0];
        }
        int len = nums.length;
        int[] ans = new int[len - k + 1];
        LinkedList<Integer> queue = new LinkedList<>();
        int index = 0;
        for (int i = 0; i < len; i++) {
            while (!queue.isEmpty() && queue.peekLast() < nums[i]) {
                queue.pollLast();
            }
            queue.offerLast(nums[i]);
            if (i >= k) {
                if (queue.peekFirst() == nums[i - k]) {
                    queue.pollFirst();
                }
            }
            if (i >= k - 1) {
                ans[index++] = queue.peekFirst();
            }
        }
        return ans;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用队列，空间复杂度O(k)

> 总结

执行用时：11 ms, 在所有 Java 提交中击败了91.52%的用户

内存消耗：46.9 MB, 在所有 Java 提交中击败了60.27%的用户
