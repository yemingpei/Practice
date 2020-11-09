### LeetCode-258-Add-Digits

> 题目链接

[LeetCode-258-Add-Digits](https://leetcode.com/problems/add-digits/)

> 思路

根据数学根的公式(num - 1) % 9 + 1求解

> 代码

```java
class Solution {
    public int addDigits(int num) {
        return (num - 1) % 9 + 1;
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Add Digits.

Memory Usage: 36.3 MB, less than 7.17% of Java online submissions for Add Digits.
