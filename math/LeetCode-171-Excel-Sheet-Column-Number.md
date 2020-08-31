### LeetCode-171-Excel-Sheet-Column-Number

> 题目链接

[LeetCode-171-Excel-Sheet-Column-Number](https://leetcode.com/problems/excel-sheet-column-number/)

> 思路

26进制转换为10进制，A字母为65，则直接减去64能得到对应10进制大小

> 代码

```java
class Solution {
    public int titleToNumber(String s) {
        int result = 0;
        for(int i = 0; i < s.length(); i++){
            result = result * 26;
            result = result + s.charAt(i) - 64;
        }
        return result;
    }
}
```

> 复杂度分析

26进制转10进制，结果部超过2 ^ 32，次数不超过8次，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Excel Sheet Column Number.

Memory Usage: 39.4 MB, less than 23.78% of Java online submissions for Excel Sheet Column Number.
