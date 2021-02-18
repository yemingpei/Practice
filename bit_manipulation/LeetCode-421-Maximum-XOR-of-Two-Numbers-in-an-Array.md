### LeetCode-421-Maximum-XOR-of-Two-Numbers-in-an-Array

> 题目链接

[LeetCode-421-Maximum-XOR-of-Two-Numbers-in-an-Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)

> 思路

不断比较，计算高进位的异或的值，然后再逐步还原最大值

> 代码

```java
class Solution {
    public int findMaximumXOR(int[] nums) {
        int maxValue = 0;
        for (int num : nums) maxValue = Math.max(maxValue, num);
        int res = 0;
        int mask = 0;
        Set<Integer> set = new HashSet<>();
        for (int i = 31 - Integer.numberOfLeadingZeros(maxValue); i >= 0; i--) {
            set.clear();
            int bit = 1 << i;
            mask |= bit;
            int temp = res | bit;
            for (int num : nums) {
                if (set.contains((num & mask) ^ temp)) {
                    res = temp;
                    break;
                }
                set.add(num & mask);
            }
        }
        return res;
    }
}
```

> 复杂度分析

最多遍历数组31遍，时间复杂度O(n)

额外使用set，空间复杂度O(n)

> 总结

Runtime: 10 ms, faster than 99.37% of Java online submissions for Maximum XOR of Two Numbers in an Array.

Memory Usage: 39.5 MB, less than 97.02% of Java online submissions for Maximum XOR of Two Numbers in an Array.
