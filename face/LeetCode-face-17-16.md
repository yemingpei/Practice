### LeetCode-face-17-16

> 题目链接

[LeetCode-face-17-16](https://leetcode-cn.com/problems/the-masseuse-lcci/)

> 思路

动态规划公式为result[i] = Math.max(result[i - 1], result[i - 2] + nums[i])

> 代码

```java
class Solution {
    public int massage(int[] nums) {
        if(nums.length == 0) return 0;
        if(nums.length == 1) return nums[0];
        int[] result = new int[nums.length];
        result[0] = nums[0];
        result[1] = Math.max(nums[0], nums[1]);
        for(int i = 2; i < nums.length; i++){
            result[i] = Math.max(result[i - 1], result[i - 2] + nums[i]);
        }
        return result[nums.length - 1];
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外int数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.8 MB, 在所有 Java 提交中击败了51.93%的用户
