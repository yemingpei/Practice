### LeetCode-598-range-addition-ii

> 题目链接

[LeetCode-598-range-addition-ii](https://leetcode-cn.com/problems/range-addition-ii/)

> 思路

寻找重叠最多的区域，就是寻找每个边的最小值

> 代码

```java
class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        int mMin = m;
        int nMin = n;
        for(int[] op:ops){
            mMin = Math.min(mMin, op[0]);
            nMin = Math.min(nMin, op[1]);
        }
        return mMin * nMin;
    }
}
```

> 复杂度分析

遍历二维数组，因为数组长度固定为2，时间复杂度O(n)

额外使用常量的int，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了5.45%的用户
