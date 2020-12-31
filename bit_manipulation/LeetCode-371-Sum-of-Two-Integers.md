### LeetCode-371-Sum-of-Two-Integers

> 题目链接

[LeetCode-371-Sum-of-Two-Integers](https://leetcode.com/problems/sum-of-two-integers/)

> 思路

与运算，筛选出进位的数，异或运算得出不需要进位的数字，相加就是两个数字的和

> 代码

```java
class Solution {
    public int getSum(int a, int b) {
        while(b != 0){
            int res = (a & b) << 1;
            a = a^b;
            b = res;              
        }
        return a;
    }
}
```

> 复杂度分析

位运算，最多进位31次，时间复杂度O(1)

额外使用两个int，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Sum of Two Integers.

Memory Usage: 35.9 MB, less than 32.00% of Java online submissions for Sum of Two Integers.
