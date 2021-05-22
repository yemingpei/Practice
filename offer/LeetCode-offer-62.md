### LeetCode-offer-62

> 题目链接

[LeetCode-offer-62](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)

> 思路

m % n就是要剔除的数字，然后把头部的数字继续拼在尾部，继续操作，直到剩下1

> 代码

```java
class Solution {
    public int lastRemaining(int n, int m) {
        int f = 0;
        for (int i = 2; i != n + 1; ++i) {
            f = (m + f) % i;
        }
        return f;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n)

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：7 ms, 在所有 Java 提交中击败了99.88%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了63.43%的用户
