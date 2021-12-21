### LeetCode-581-shortest-unsorted-continuous-subarray

> 题目链接

[LeetCode-581-shortest-unsorted-continuous-subarray](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/)

> 思路

先寻找需要更换的最大值和最小值，再确定更换的起始和结束的位置

> 代码

```java
class Solution {
    public int findUnsortedSubarray(int[] nums) {
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;
        for(int i = 1; i < nums.length; i++){
            if(nums[i] < nums[i - 1]){
                min = Math.min(min, nums[i]);
                max = Math.max(max, nums[i - 1]);
            }
        }
        if(min == Integer.MAX_VALUE) return 0;
        int start = 0, end = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] > min){
                start = i;
                break;
            }
        }
        for(int i = nums.length - 1; i > -1; i--){
            if(nums[i] < max){
                end = i;
                break;
            }
        }
        return end - start + 1;
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

额外使用常数的变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.97%的用户

内存消耗：39.3 MB, 在所有 Java 提交中击败了89.20%的用户
