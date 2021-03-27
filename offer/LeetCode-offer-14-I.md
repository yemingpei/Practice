### LeetCode-offer-14-I

> 题目链接

[LeetCode-offer-14-I](https://leetcode-cn.com/problems/jian-sheng-zi-lcof/)

> 思路

根据算术几何均值不等式和极大值，分成为3一小段，能达到最大值

> 代码

```java
class Solution {
    public int cuttingRope(int n) {
        if(n < 4) return n - 1;
        int a = n / 3, b = n % 3;
        if(b == 0) return (int)Math.pow(3, a);
        if(b == 1) return (int)Math.pow(3, a - 1) * 4;
        return (int)Math.pow(3, a) * 2;
    }
}
```

> 复杂度分析

公式法计算，时间复杂度O(1)

额外使余数和商，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.4 MB, 在所有 Java 提交中击败了20.51%的用户
