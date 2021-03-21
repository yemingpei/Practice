### LeetCode-offer-10

> 题目链接

[LeetCode-offer-10](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/)

> 思路

用循环代替递归，节省函数栈的空间

> 代码

```java
class Solution {
    public int fib(int n) {
        int e = 1000000007;
        if(n == 0) return 0;
        if(n == 1) return 1;
        int f1 = 0;
        int f2 = 1;
        for(int i = 1; i < n; i++){
            f2 = f2 + f1;
            f1 = f2 - f1;
            f2 = f2 % e;
        }
        return  f2;
    }
}
```

> 复杂度分析

循环操作，时间复杂度O(n)

只保存两个常量值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.1 MB, 在所有 Java 提交中击败了80.12%的用户

