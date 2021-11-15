### LeetCode-509-fibonacci-number

> 题目链接

[LeetCode-509-fibonacci-number](https://leetcode-cn.com/problems/fibonacci-number/)

> 思路

利用循环代替递归，减少计算次数和栈空间

> 代码

```java
class Solution {
    public int fib(int n) {
        if(n == 0) return 0;
        if(n == 1) return 1;
        int a = 0;
        int b = 1;
        for(int i = 1; i < n; i++){
            int sum = a + b;
            a = b;
            b = sum;
        }
        return b;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用常量类型，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：34.7 MB, 在所有 Java 提交中击败了99.09%的用户
