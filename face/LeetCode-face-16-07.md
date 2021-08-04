### LeetCode-face-16-07

> 题目链接

[LeetCode-face-16-07](https://leetcode-cn.com/problems/maximum-lcci/)

> 思路

利用位运算，先确定符号，然后利用绝对值的原理来完成输出最大值

> 代码

```java
class Solution {
    public int maximum(int a, int b) {
        int k = b - a >>> 31;
        int aSign = a >>> 31, bSign = b >>> 31;
        int diff = aSign ^ bSign;
        k = k & (diff ^ 1) | bSign & diff;
        return a * k + b * (k ^ 1);
    }
}
```

> 复杂度分析

位运算，时间复杂度O(1)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.1 MB, 在所有 Java 提交中击败了70.84%的用户
