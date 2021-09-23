### LeetCode-462-minimum-moves-to-equal-array-elements-ii

> 题目链接

[LeetCode-462-minimum-moves-to-equal-array-elements-ii](https://leetcode-cn.com/problems/minimum-moves-to-equal-array-elements-ii/)

> 思路

利用排序，取中位数，计算转换的次数，count = Math.abs(mid - nums[i])，化简为ans += nums[right] - nums[left]

> 代码

```java
class Solution {
    public int minMoves2(int[] nums) {
        Arrays.sort(nums);
        int ans = 0;
        for (int i = 0, j = nums.length - 1; i < j; i++, j--) ans += nums[j] - nums[i];
        return ans;
    }
}
```

> 复杂度分析

使用排序，时间复杂度O(nlogn)

额外使用int辅助计算，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了82.29%的用户
