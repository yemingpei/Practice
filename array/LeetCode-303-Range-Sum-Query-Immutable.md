### LeetCode-303-Range-Sum-Query-Immutable

> 题目链接

[LeetCode-303-Range-Sum-Query-Immutable](https://leetcode.com/problems/range-sum-query-immutable/)

> 思路

保存前n个数之和，利用公式result[j] - result[i - 1]计算i，j的区间和，i等于0就直接返回

> 代码

```java
class NumArray {
    private int[] result;
    public NumArray(int[] nums) {
        result = new int[nums.length];
        int sum = 0;
        for(int i = 0; i < nums.length; i++){
            sum += nums[i];
            result[i] = sum;
        }
    }  
    public int sumRange(int i, int j) {
        if(i == 0) return result[j];
        else return result[j] - result[i - 1];
    }
}
```

> 复杂度分析

构造函数，时间复杂度O(n)，sumRange函数，时间复杂度为O(1)

用数组保存前n个数之和，空间复杂度O(n)

> 总结

Runtime: 6 ms, faster than 100.00% of Java online submissions for Range Sum Query - Immutable.

Memory Usage: 41.7 MB, less than 89.32% of Java online submissions for Range Sum Query - Immutable.
