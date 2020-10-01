### LeetCode-209-Minimum-Size-Subarray-Sum

> 题目链接

[LeetCode-121-Best-Time-to-Buy-and-Sell-Stock](https://leetcode.com/problems/minimum-size-subarray-sum/)

> 思路

暴力法，一一比较，寻找最短的距离

> 代码

```java
class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        int len=0;
        int i=0;
        int sum=0;
        int j=0;
        while(j<nums.length){
            sum+=nums[j];
            while(sum>=s){
                len=len==0?(j-i+1):Math.min(len,j-i+1);
                sum-=nums[i];
                i++;
            }
            j++;
        }
        return len;
    }
}
```

> 复杂度分析

暴力法遍历数组，时间复杂度O(n ^ 2)

需要四个常量int来辅助记录，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Minimum Size Subarray Sum.

Memory Usage: 39.1 MB, less than 94.06% of Java online submissions for Minimum Size Subarray Sum.
