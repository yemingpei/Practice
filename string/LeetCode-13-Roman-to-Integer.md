### LeetCode-13-Roman-to-Integer

> 题目链接

[LeetCode-13-Roman-to-Integer](https://leetcode.com/problems/roman-to-integer/)

> 思路

当一个比后一个字母小的时候，表示的是相减，从后面开始遍历

> 代码

```java
class Solution {
    public static int romanToInt(String s) {
        int res = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            char c = s.charAt(i);
            switch (c) {
            case 'I':
                res += (res >= 5 ? -1 : 1);
                break;
            case 'V':
                res += 5;
                break;
            case 'X':
                res += 10 * (res >= 50 ? -1 : 1);
                break;
            case 'L':
                res += 50;
                break;
            case 'C':
                res += 100 * (res >= 500 ? -1 : 1);
                break;
            case 'D':
                res += 500;
                break;
            case 'M':
                res += 1000;
                break;
            }
        }
        return res;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用sum记录，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Roman to Integer.

Memory Usage: 39.8 MB, less than 58.27% of Java online submissions for Roman to Integer.
