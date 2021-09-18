### LeetCode-453-minimum-moves-to-equal-array-elements

> 题目链接

[LeetCode-453-minimum-moves-to-equal-array-elements](https://leetcode-cn.com/problems/minimum-moves-to-equal-array-elements/)

> 思路

每次操作n-1个数字增加1，和操作一个数字-1的效果是一致的，都是该数和其他数字的差距缩小1

> 代码

```java
class Solution {
    public int minMoves(int[] nums) {
        int moves = 0, min = Integer.MAX_VALUE;
        for (int i = 0; i < nums.length; i++) {
            min = Math.min(min, nums[i]);
        }
        for (int i = 0; i < nums.length; i++) {
            moves += nums[i] - min;
        }
        return moves;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了70.18%的用户
