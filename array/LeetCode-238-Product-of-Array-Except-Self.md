### LeetCode-238-Product-of-Array-Except-Self

> 题目链接

[LeetCode-238-Product-of-Array-Except-Self](https://leetcode.com/problems/product-of-array-except-self/)

> 思路

```java
数组                    a = {2, 2, 3, 4, 5}
第一遍遍历result为  result = {1, 2, 4, 12, 48}
然后再从右到左      result = {120, 120, 80, 60, 48}
```

分拆问题为i位置的结果为左右两边乘积相乘，先遍历数组，把position左边的乘先保存好，然后用right保存右边的乘积，还原结果数组

> 代码

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int length = nums.length;
        int[] result = new int[length];
        if(length == 0) return result;
        result[0] = 1;
        for(int i = 1; i < length; i++)
            result[i] = result[i - 1] * nums[i - 1];
        int right = nums[length - 1];
        for(int i = length - 2; i >= 0; i--){
            result[i] = result[i] * right;
            right *= nums[i];
        }
        return result;
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

需要一个常量int来右边的乘积，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.99% of Java online submissions for Product of Array Except Self.

Memory Usage: 50.1 MB, less than 20.00% of Java online submissions for Product of Array Except Self.
