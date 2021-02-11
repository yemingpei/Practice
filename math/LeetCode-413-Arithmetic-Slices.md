### LeetCode-413-Arithmetic-Slices

> 题目链接

[LeetCode-413-Arithmetic-Slices](https://leetcode.com/problems/arithmetic-slices/)

> 思路

如果相同的差值有k个，那肯定会有k*(k+1)/2个组合

> 代码

```java
class Solution {
    public int numberOfArithmeticSlices(int[] A) {
        int count = 0;
        int sum = 0;
        for (int i = 2; i < A.length; i++) {
            if (A[i] - A[i - 1] == A[i - 1] - A[i - 2]) {
                count++;
            } else {
                sum += (count + 1) * (count) / 2;
                count = 0;
            }
        }
        return sum += count * (count + 1) / 2;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外两个int常量，空间复杂度O(1)。

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Arithmetic Slices.

Memory Usage: 36.6 MB, less than 82.28% of Java online submissions for Arithmetic Slices.
