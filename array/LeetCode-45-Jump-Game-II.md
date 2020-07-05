### LeetCode-45-Jump-Game-II

> 题目链接

[LeetCode-45-Jump-Game-II](https://leetcode.com/problems/jump-game-ii/)

> 思路

先看几个例子

模拟跳的格数，寻找每一步所能达到的最远距离

> 代码

```java
class Solution {
    public int jump(int[] nums) {
        if(nums.length == 1) return 0;
        int count = 0;
        int step = 0;
        while(step < nums.length){
            int max = 0;
            int end = step + nums[step];
            if(end >= nums.length -1) return count + 1;
            for(int i = step + 1; i <= end; i++){
                int length = i + nums[i];
                if(length > max ){
                    max = length;
                    step = i;
                }
            }
            count++;
        }
        return count;
    }
}
```

> 复杂度分析

从头到尾执行一遍，应该为O(n)

额外使用4个int辅助记录，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 93.32% of Java online submissions for Jump Game II.

Memory Usage: 41.2 MB, less than 75.93% of Java online submissions for Jump Game II.
