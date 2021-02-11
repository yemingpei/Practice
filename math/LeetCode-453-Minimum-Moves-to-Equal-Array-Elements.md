### LeetCode-453-Minimum-Moves-to-Equal-Array-Elements

> 题目链接

[LeetCode-453-Minimum-Moves-to-Equal-Array-Elements](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/)

> 思路

最小值，没操作一次，就会追回一次，要寻找最小值的和

> 代码

```java
class Solution {
    public int minMoves(int[] nums) {
        int min = nums[0];
        for(int n : nums){
            min = Math.min(min, n);
        }
        int res = 0;
        for(int n : nums){
            res += n-min;
        }
        return res;
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

无额外使用其他变量，空间复杂度O(1)。

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Minimum Moves to Equal Array Elements.

Memory Usage: 39.4 MB, less than 58.49% of Java online submissions for Minimum Moves to Equal Array Elements.
