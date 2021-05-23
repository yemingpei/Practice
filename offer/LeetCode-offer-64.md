### LeetCode-offer-64

> 题目链接

[LeetCode-offer-64](https://leetcode-cn.com/problems/qiu-12n-lcof/)

> 思路

利用栈代替循环，然后一次相加

> 代码

```java
class Solution {
    public int sumNums(int n) {
        boolean flag = n > 0 && (n += sumNums(n - 1)) > 0;
        return n;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n)

函数栈的深度是n，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.7 MB, 在所有 Java 提交中击败了47.27%的用户
