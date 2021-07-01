### LeetCode-face-05-01

> 题目链接

[LeetCode-face-05-01](https://leetcode-cn.com/problems/insert-into-bits-lcci/)

> 思路

一次替换i到j位置的二进制的数字

> 代码

```java
class Solution {
    public int insertBits(int N, int M, int i, int j) {
        for(int start = i; start <= j; start++){
            if((M & 1) == 1) N = (1 << start) | N;
            else N = (~(1 << start)) & N;
            M = M >> 1;
        }
        return N;
    }
}
```

> 复杂度分析

位运算，时间复杂度O(1) 

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了26.07%的用户
