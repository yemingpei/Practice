### LeetCode-41-First-Missing-Positive

> 题目链接

[LeetCode-41-First-Missing-Positive](https://leetcode.com/problems/first-missing-positive/)

> 思路

先看几个例子

利用原数组来存在正确的数据，就是i的位置的数据是i+1则是正确的

> 代码

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        for(int i=0; i < nums.length; i++){
            while(nums[i] != (i+1) && nums[i] > 0 && nums[i] <= nums.length && nums[nums[i]-1] != nums[i]){
                int swap = nums[nums[i]-1];
                nums[nums[i]-1] = nums[i];
                nums[i] = swap;
            }
        }
        for(int i = 0; i < nums.length; i++)
                if(nums[i] != (i +1))
                    return i+1;
        return nums.length + 1;
    }
}
```

> 复杂度分析

最多执行3n遍，应该为O(n)

在原数组上操作，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 63.16% of Java online submissions for First Missing Positive.

Memory Usage: 39.1 MB, less than 13.86% of Java online submissions for First Missing Positive.
