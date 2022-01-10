### LeetCode-628-maximum-product-of-three-numbers

> 题目链接

[LeetCode-628-maximum-product-of-three-numbers](https://leetcode-cn.com/problems/maximum-product-of-three-numbers/)

> 思路

因为要寻找最大的数字，就有两个可能，三个最大的整数或者是两个最小的负数和一个最大的正数

> 代码

```java
class Solution {
    public int maximumProduct(int[] nums) {
        int min1 = Integer.MAX_VALUE;
        int min2 = Integer.MAX_VALUE;
        int max1 = Integer.MIN_VALUE;
        int max2 = Integer.MIN_VALUE;
        int max3 = Integer.MIN_VALUE;
        for(int num : nums){
           if(num < min1){
               min2 = min1;
               min1 = num;
           }else if(num < min2){
               min2 = num;
           }

           if(num > max1){
               max3 = max2;
               max2 = max1;
               max1 = num;
           }else if(num > max2){
               max3 = max2;
               max2 = num;
           }else if(num > max3){
               max3 = num;
           }
        }
        return Math.max(max1*max2*max3,max1*min1*min2);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int变量辅助，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.18%的用户

内存消耗：39.4 MB, 在所有 Java 提交中击败了96.73%的用户
