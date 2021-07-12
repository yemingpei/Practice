### LeetCode-face-08-05

> 题目链接

[LeetCode-face-08-05](https://leetcode-cn.com/problems/recursive-mulitply-lcci/)

> 思路

不断位移，如果遇上1就需要做加法，否则，减法

> 代码

```java
class Solution {
    public int multiply(int A, int B) {
        if(A > B) return multi(A, B);
        else return multi(B, A);
    }
    public int multi(int A, int B) {
        if(B == 1) return A;
        if((B & 1) == 1) return multi(A << 1, B >> 1) + A;
        else return multi(A << 1, B >> 1);
    }
}
```

> 复杂度分析

最多位移32次，时间复杂度O(1) 

额外使用不超过32次的栈空间，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了27.16%的用户
