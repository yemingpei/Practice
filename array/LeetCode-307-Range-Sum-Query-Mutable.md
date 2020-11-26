### LeetCode-307-Range-Sum-Query-Mutable

> 题目链接

[LeetCode-307-Range-Sum-Query-Mutable](https://leetcode.com/problems/range-sum-query-mutable/)

> 思路

树状数组，分段保存数据之和，然后通过分段相减得出区间之和

> 代码

```java
class NumArray {
    private int[] preSum;
    private int[] nums;
    public NumArray(int[] nums) {
        this.nums = nums;
        this.preSum = new int[nums.length + 1];
        for (int i = 0; i < nums.length; ++i) {
            preSum[i + 1] = nums[i];
        }
        for (int i = 1; i < preSum.length; ++i) {
            int j = i + (i & -i);
            if (j < preSum.length) {
                preSum[j] += preSum[i];
            }
        }
    }
    public void update(int i, int val) {
        int diff = val - nums[i];
        nums[i] = val;
        int n = i + 1;
        while (n < preSum.length) {
            preSum[n] += diff;
            n += (n & (-n));
        }
    }
    public int sumRange(int i, int j) {
        return sum(j + 1) - sum(i);
    }
    private int sum(int n) {
        int sum = 0;
        while (n != 0) {
            sum += preSum[n];
            n &= (n - 1);  
        }
        return sum;
    }
}
```

> 复杂度分析

构造函数，时间复杂度O(n),update函数时间复杂度O(logn),sumRange函数时间复杂度O(logn)

需要保存树状数组的形态变量，空间复杂度O(n)

> 总结

Runtime: 10 ms, faster than 78.44% of Java online submissions for Range Sum Query - Mutable.

Memory Usage: 44.8 MB, less than 77.79% of Java online submissions for Range Sum Query - Mutable.
