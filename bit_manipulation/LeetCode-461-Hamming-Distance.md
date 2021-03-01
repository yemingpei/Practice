### LeetCode-461-Hamming-Distance

> 题目链接

[LeetCode-461-Hamming-Distance](https://leetcode.com/problems/hamming-distance/)

> 思路

使用x = x & (x - 1)移除右边的1，来计算1的个数

> 代码

```java
class Solution {
    public int hammingDistance(int x, int y) {
        int count = 0;
        int flag = x ^ y;
        while(flag != 0){
            flag = flag & (flag - 1);
            count++;
        }
        return count;
    }
}
```

> 复杂度分析

使用位运算，时间复杂度O(1)

额外使用count计数，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Hamming Distance.

Memory Usage: 35.5 MB, less than 88.81% of Java online submissions for Hamming Distance.
