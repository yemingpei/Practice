### LeetCode-137-Single-Number-II

> 题目链接

[LeetCode-137-Single-Number-II](https://leetcode.com/problems/single-number-ii/)

> 思路

int为32位，遍历每个数的指定位，如果能整除3，那输出位上，该位为0，否则为1

> 代码

```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for(int i = 0; i < 32; i++){
            int sum = 0;
            for(int j = 0; j < nums.length; j++)
                    sum += (nums[j] >>> i) & 1;
            if(sum % 3 != 0)
                result = result | (1 << i);
        }
        return result;
    }
}
```

> 复杂度分析

遍历了32 * n次，时间复杂度O(n)

额外使用有int数据辅助，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 65.19% of Java online submissions for Single Number II.

Memory Usage: 39.6 MB, less than 21.51% of Java online submissions for Single Number II.
