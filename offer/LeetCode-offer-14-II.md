### LeetCode-offer-14-II

> 题目链接

[LeetCode-offer-14-II](https://leetcode-cn.com/problems/jian-sheng-zi-ii-lcof/)

> 思路

根据算术几何均值不等式和极大值，分成为3一小段，能达到最大值

> 代码

```java
class Solution {
    public int cuttingRope(int n) {
        if(n < 4) return n - 1;
        int a = n / 3, b = n % 3;
        if(b == 0) return myPow(3, a, 1);
        else if(b == 1) return myPow(3, a - 1, 4);
        else return myPow(3, a, 2);
    }
    public int myPow(int number, int pow, int other){
        long result = other;
        for(int i = 0; i < pow; i++){
            result *= number;
            result = result % 1000000007;
        }
        return (int)result;
    }
}
```

> 复杂度分析

求余数，时间复杂度O(n)

额外使余数和商，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.4 MB, 在所有 Java 提交中击败了20.51%的用户
