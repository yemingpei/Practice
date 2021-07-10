### LeetCode-face-08-01

> 题目链接

[LeetCode-face-08-01](https://leetcode-cn.com/problems/three-steps-problem-lcci/)

> 思路

斐波那契，f(n) = f(n - 1) + f(n - 2) + f(n - 3)

> 代码

```java
class Solution {
    public int waysToStep(int n) {
        if(n == 1) return 1;
        if(n == 2) return 2;
        if(n == 3) return 4;
        int f1 = 1, f2 = 2, f3 = 4;
        for(int i = 3; i < n; i++){
            int a = f3;
            f3 = ((f1 + f2) % 1000000007 + f3) % 1000000007;
            f1 = f2;
            f2 = a;
        }
        return f3;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n) 

额外使用三个常量变量，空间复杂度O(1)

> 总结

执行用时：12 ms, 在所有 Java 提交中击败了99.04%的用户

内存消耗：35.1 MB, 在所有 Java 提交中击败了90.86%的用户
