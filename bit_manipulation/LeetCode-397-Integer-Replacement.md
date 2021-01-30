### LeetCode-397-Integer-Replacement

> 题目链接

[LeetCode-397-Integer-Replacement](https://leetcode.com/problems/integer-replacement/)

> 思路

偶数的话，就右移，奇数的话，就看是不是3，刚好是3就-1，否则末尾是11就+1，特殊处理最大值

> 代码

```java
class Solution {
    public int integerReplacement(int n) {
        if(n == Integer.MAX_VALUE) return 32;
        int count = 0;
        while(n != 1){
            if((n & 1) == 0){
                n >>= 1;
            }else if((n & 3) == 3 && n != 3){
                n++;
            }else{
                n--;
            }
            count++;
        }
        return count;
    }
}
```

> 复杂度分析

最多运行32次，时间复杂度O(1)

无额外使用变量值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Integer Replacement.

Memory Usage: 35.6 MB, less than 89.50% of Java online submissions for Integer Replacement.
