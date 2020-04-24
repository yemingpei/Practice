### LeetCode-239-Sliding-Window-Maximum

> 题目链接

[LeetCode-239-Sliding-Window-Maximum](https://leetcode.com/problems/sliding-window-maximum/)

> 思路

窗口K，先记录前k个，最大值，和最大值的位置。然后移动的时候，下一个值，比原来的最大值大，直接改变的最大值，如果比最大值小，且原来的最大值还在窗口内，则
最大值不变，否则遍历新的窗口寻找最大值。

> 代码

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if (nums.length < 1) return nums;
        int max = nums[0];
        int maxIndex = 0;
        int[] result = new int[nums.length - k + 1];
        int index = 0;
        for (int i = 0; i < k; i++)
          if (nums[i] > max) {
            max = nums[i];
            maxIndex = i;
          }
        result[index++] = max;
        for (int i = k; i < nums.length; i++) {
          if (nums[i] >= max) {
            max = nums[i];
            maxIndex = i;
            result[index++] = max;
          } else if (maxIndex >= (i - k + 1)) {
            result[index++] = max;
          } else {
            maxIndex =(i - k + 1);
            max =nums[maxIndex];
            for (int start = maxIndex+1 ; start <= i; start++) {
              if (nums[start] > max) {
                max = nums[start];
                maxIndex = start;
              }
            }
            result[index++] = max;
          }
        }
        return result;
    }
}
```

> 复杂度分析

循环遍历了一遍数组，最优的情况是n，是个递增的数组，最坏情况是n * k 是个递减的数组，均摊时间复杂度O(n)

额外使用一个int数组辅助，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Sliding Window Maximum.
Memory Usage: 47.7 MB, less than 6.25% of Java online submissions for Sliding Window Maximum.
