### LeetCode-279-Perfect-Squares

> 题目链接

[LeetCode-279-Perfect-Squares](https://leetcode.com/problems/perfect-squares/)

> 思路

根据四平方数原理，一个数可以分成四个平方数的和，所以输出结果为1到4其中一个，本身为平方数和两个平方数则用是否可以平方来解决，为四个平方数的满足公式n = 4 ^ k * (8m + 7)

> 代码

```java
class Solution {
    public boolean isSquat(int i){
        int j = (int)Math.sqrt(i);
        return i == j * j;
    }
    public int numSquares(int n) {
        while(n % 4 == 0)
            n /= 4;
        if(n % 8 == 7) return 4;
        if(isSquat(n)) return 1;
        for(int i = 1; i * i < n; i++){
            if(isSquat(n - i * i)) return 2;
        }
        return 3;
    }
}
```

> 复杂度分析

最坏情况为logn，时间复杂度O(logn)，返回1和4的时候，时间复杂度为O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Perfect Squares.

Memory Usage: 35.9 MB, less than 5.35% of Java online submissions for Perfect Squares.
