### LeetCode-169-Majority-Element

> 题目链接

[LeetCode-169-Majority-Element](https://leetcode.com/problems/majority-element/)

> 思路

数组必有某个二进制位的个数大于n / 2,利用int的长度是32来筛选要找的数。

> 代码

```java
class Solution {
    public int majorityElement(int[] nums) {
        int n = nums.length;
        int ans = 0;
        for (int i = 31; i >= 0 ; i --) {
            int bit = 0;
            int a = 1 << i;
            for (int j = 0; j < n; j ++) {
                if ((nums[j] & (a)) == 0) {
                    bit ++;
                }
            }
            ans <<= 1;
            ans += (bit > (n >> 1)) ? 0 : 1;
        }
        return ans;
    }
}
```

> 复杂度分析

遍历一次数组，时间复杂度O(n)

额外使用有int辅助，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 93.19% of Java online submissions for Majority Element.

Memory Usage: 42.9 MB, less than 70.20% of Java online submissions for Majority Element.
