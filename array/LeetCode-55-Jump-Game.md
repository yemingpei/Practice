### LeetCode-55-Jump-Game

> 题目链接

[LeetCode-55-Jump-Game](https://leetcode.com/problems/jump-game/)

> 思路

寻找最大步数，若存在最大步数的位置是0，无解，返回false，能到达尾部则有解

> 代码

```java
class Solution {
    public boolean canJump(int[] nums) {
        return jump(nums, 0);
    }
    public boolean jump(int[] nums ,int n){
        if(n >= nums.length -1) return true;
        if(n + nums[n] >= nums.length) return true;
        if(nums[n] == 0) return false;
        int max = 0;
        int position = n;
        for(int i = 1; i <= nums[n]; i++){
           int length = i + nums[n + i];
            if(max < length){
                max = length;
                position = n + i;
            }
        }
        return jump(nums, position);
    }
}
```

> 复杂度分析

遍历了一遍数组，时间复杂度O(n)

额外使用三个int值来辅助，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.12% of Java online submissions for Jump Game.

Memory Usage: 43.1 MB, less than 28.85% of Java online submissions for Jump Game.
