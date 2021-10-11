### LeetCode-479-largest-palindrome-product

> 题目链接

[LeetCode-479-largest-palindrome-product](https://leetcode-cn.com/problems/largest-palindrome-product/)

> 思路

从max - 1开始，构造最大的回文字符串，然后倒推对应的数字

> 代码

```java
class Solution {
    public int largestPalindrome(int n) {
        if(n == 1) return 9;
        long max = (long) Math.pow(10, n) - 1;
        for(long i = max - 1; i > max / 10; i--){
            String s1 = String.valueOf(i);
            long rev = Long.parseLong(s1 + new StringBuilder(s1).reverse().toString());
            for(long x = max; x * x >= rev; x --){
                if(rev % x == 0) return (int)(rev % 1337);
            }
        }
        return -1;
    }
}
```

> 复杂度分析

需要遍历，时间复杂度O(10 ^ n)

额外使用long辅助，空间复杂度O(1)

> 总结

执行用时：93 ms, 在所有 Java 提交中击败了58.16%的用户

内存消耗：37.6 MB, 在所有 Java 提交中击败了28.57%的用户
