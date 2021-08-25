### LeetCode-face-17-06

> 题目链接

[LeetCode-face-17-06](https://leetcode-cn.com/problems/number-of-2s-in-range-lcci/)

> 思路

从个位开始依次向高位遍历, 用每一位的数字与遍历过的位数所存在的 2 的次数相乘, 再判断新的一位是否为 2, 如果为 2 或者大于 2 则增加相应记录数.

> 代码

```java
class Solution {
    public int numberOf2sInRange(int n) {
        int sum = 0,base = 1,left = 0;
        while(n != 0){
            int val = n % 10;
            n /= 10;
            sum += base * n;
            if(val == 2) sum += left + 1;
            else if(val > 2) sum += base;
            left += base * val;
            base *= 10;
        }
        return sum;
    }
}
```

> 复杂度分析

不断除以10，时间复杂度O(logn)

额外使用int值的变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了39.81%的用户
