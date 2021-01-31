### LeetCode-410-Split-Array-Largest-Sum

> 题目链接

[LeetCode-410-Split-Array-Largest-Sum](https://leetcode.com/problems/split-array-largest-sum/)

> 思路

二分的上界为数组nums 中所有元素的和，下界为数组 nums 中所有元素的最大值。通过二分查找，我们可以得到最小的最大分割子数组和，这样就可以得到最终的答案

> 代码

```java
class Solution {
    public int splitArray(int[] nums, int m) {
        int left = 0, right = 0;
        for (int i = 0; i < nums.length; i++) {
            right += nums[i];
            if (left < nums[i]) {
                left = nums[i];
            }
        }
        while (left < right) {
            int mid = (right - left) / 2 + left;
            if (check(nums, mid, m)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }

    public boolean check(int[] nums, int x, int m) {
        int sum = 0;
        int cnt = 1;
        for (int i = 0; i < nums.length; i++) {
            if (sum + nums[i] > x) {
                cnt++;
                sum = nums[i];
            } else {
                sum += nums[i];
            }
        }
        return cnt <= m;
    }
}
```

> 复杂度分析

maxn 表示数组所有元素的最大值。每次二分查找时，需要对数组进行一次遍历，时间复杂度为 O(n)，时间复杂度O(n×log(sum−maxn))

无额外使用变量值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Split Array Largest Sum.

Memory Usage: 36.1 MB, less than 97.48% of Java online submissions for Split Array Largest Sum.
