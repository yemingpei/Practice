### LeetCode-offer-56-II

> 题目链接

[LeetCode-offer-56-II](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

> 思路

有限状态转换，利用两个数来完成这个转换ones = ones ^ num & ~twos，twos = twos ^ num & ~ones;

> 代码

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ones = 0, twos = 0;
        for(int num : nums){
            ones = ones ^ num & ~twos;
            twos = twos ^ num & ~ones;
        }
        return ones;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用两个int标志位标志，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了90.08%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了99.52%的用户
