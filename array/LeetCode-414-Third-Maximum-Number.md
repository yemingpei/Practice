### LeetCode-414-Third-Maximum-Number

> 题目链接

[LeetCode-414-Third-Maximum-Number](https://leetcode.com/problems/third-maximum-number/)

> 思路

不断比较三个值的大小，初始值为Integer.MIN_VALUE，用一个boolean记录最小值有没有出现过，如果有比较第二和第三是否相等，不相等，则返回最大值，如果没有就看第三大的数是不是最小值就知道返回最大值还是第三大的值

> 代码

```java
class Solution {
    public int thirdMax(int[] nums) {
        int tmax = Integer.MIN_VALUE;
        int smax = Integer.MIN_VALUE;
        int max = nums[0];
        boolean minValue = max == Integer.MIN_VALUE;
        for(int i = 1; i<nums.length; i++) {
            if(nums[i] == Integer.MIN_VALUE) minValue = true;
            if(nums[i] > max) {
                tmax = smax;
                smax = max;
                max = nums[i];
            } else if(nums[i] < max && nums[i] > smax) {
                tmax = smax;
                smax = nums[i];
            } else if(nums[i] < smax && nums[i] > tmax) {
                tmax = nums[i];
            }
        }
        if(minValue) return smax == tmax ? max: tmax;
        else return tmax == Integer.MIN_VALUE? max: tmax;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要三个个常量int来记录最小值和最大收益，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Third Maximum Number.

Memory Usage: 39.4 MB, less than 17.92% of Java online submissions for Third Maximum Number.
