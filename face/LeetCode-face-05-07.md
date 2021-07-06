### LeetCode-face-05-07

> 题目链接

[LeetCode-face-05-07](https://leetcode-cn.com/problems/exchange-lcci/)

> 思路

先把奇位的数字选出来，左移；然后再把偶位的数字选出来，右移。

> 代码

```java
class Solution {
    public int exchangeBits(int num) {
        return (((num & 0x55555555) << 1) | ((num & 0xaaaaaaaa) >> 1));
    }
}
```

> 复杂度分析

位运算，时间复杂度O(1) 

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35 MB, 在所有 Java 提交中击败了89.68%的用户
