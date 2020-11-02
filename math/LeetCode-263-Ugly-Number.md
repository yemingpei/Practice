### LeetCode-263-Ugly-Number
> 题目链接

[LeetCode-263-Ugly-Number](https://leetcode.com/problems/ugly-number/)

> 思路

检查是否有因子2，3，5，如果不能整除，最后n不等于1，返回失败

> 代码

```java
class Solution {
    public boolean isUgly(int num) {
        if(num < 1) return false;
        while(num % 2 == 0){
            num /= 2;
        }
        while(num  % 3 == 0){
            num /= 3;
        }
        while(num  % 5 == 0){
            num /= 5;
        }
        return num == 1;
    }
}
```

> 复杂度分析

最多循环32次，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Ugly Number.

Memory Usage: 36.3 MB, less than 7.21% of Java online submissions for Ugly Number.
