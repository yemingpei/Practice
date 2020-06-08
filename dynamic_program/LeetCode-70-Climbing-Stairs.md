### LeetCode-70-Climbing-Stairs

> 题目链接

[LeetCode-70-Climbing-Stairs](https://leetcode.com/problems/climbing-stairs/)

> 思路

推导公式f(n) = f(n-1) + f(n-2),f(1) = 1,f(2) = 2,不做重复运算，用循环计算，不使用递归

> 代码

```java
class Solution {
    public int climbStairs(int n) {
        if(n == 1) return 1;
        if(n == 2) return 2;
        int first = 1;
        int second = 2;
        for(int i = 3;i <= n;i++){
            int sum = first + second;
            first = second;
            second = sum;
        }
        return second;
    }
}
```

> 复杂度分析

从1，计算到n，时间复杂度O(n)

额外使用了sum和first和second的辅助指针，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Climbing Stairs.

Memory Usage: 35.9 MB, less than 91.03% of Java online submissions for Climbing Stairs.
