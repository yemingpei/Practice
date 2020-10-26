### LeetCode-260-Single-Number-III

> 题目链接

[LeetCode-260-Single-Number-III](https://leetcode.com/problems/single-number-iii/)

> 思路

先异或预算，找出两个不同的值的异或，然后用result & (-result)来获取最右边的1，再通过这个位数为1，进行分组，过滤出其中的一个值，再异或还原另一个值

> 代码

```java
class Solution {
    public int[] singleNumber(int[] nums) {
        int result = 0;
        for(int num : nums) result ^= num;
        int bit = result & (-result);
        int x = 0;
        for(int num : nums){
            if((num & bit) == bit) x ^= num;
        }
        return new int[]{x, result ^ x};
    }
}
```

> 复杂度分析

遍历了两遍数组，时间复杂度O(n)

使用了三个int值来辅助，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 98.88% of Java online submissions for Single Number III.

Memory Usage: 39 MB, less than 5.26% of Java online submissions for Single Number III.
