### LeetCode-offer-61

> 题目链接

[LeetCode-offer-61](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)

> 思路

用二进制来保存数据，来确认是否有相同的数据，寻找最大和最小值，然后比较他们的差值，是否小于4

> 代码

```java
class Solution {
    public boolean isStraight(int[] nums) {
        int visited = 0;
        int max = 1, min = 14;
        for (int num : nums) {
            if (num == 0) continue;
            int mask = 1 << num;
            if ((visited & mask) != 0) return false;
            visited |= mask;
            max = Math.max(max, num);
            min = Math.min(min, num);
        }
        return max - min <= 4;
    }
}
```

> 复杂度分析

因为只有5个数，有限的次数，时间复杂度O(1)

额外使用常量来保存位运算的位置，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了33.69%的用户
