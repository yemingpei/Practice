### LeetCode-532-k-diff-pairs-in-an-array

> 题目链接

[LeetCode-532-k-diff-pairs-in-an-array](https://leetcode-cn.com/problems/k-diff-pairs-in-an-array/)

> 思路

排序，然后利用双指针移动，不断寻找目标值

> 代码

```java
class Solution {
    public int findPairs(int[] nums, int k) {
        Arrays.sort(nums);
        int left = 0;
        int right = 1;
        int ans = 0;
        while (right < nums.length) {
            while (left < right - 1 && nums[right] - nums[left] > k) {
                left++;
            }
            if (nums[right] - nums[left] == k) {
                ans++;
                while (right < nums.length && nums[right] - nums[left] == k) {
                    right++;
                }
            } else {
                right++;
            }           
        }
        return ans;
    }
}
```

> 复杂度分析

使用排序，时间复杂度O(nlogn)

额外使用常量，空间复杂度O(1)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了99.80%的用户

内存消耗：37.7 MB, 在所有 Java 提交中击败了99.19%的用户
