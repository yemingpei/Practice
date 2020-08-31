### LeetCode-168-Excel-Sheet-Column-Title

> 题目链接

[LeetCode-168-Excel-Sheet-Column-Title](https://leetcode.com/problems/excel-sheet-column-title/)

> 思路

转换为26进制，一共26个字母，先用n-1，这样 0 ~ 25，正好代表26个字母

> 代码

```java
class Solution {
    public String convertToTitle(int n) {
        StringBuilder result = new StringBuilder();
        while(n != 0){
            n = n - 1;
            int count = n % 26;
            n = n / 26;
            result.insert(0, (char)('A' + count));
        }
        return result.toString();
    }
}
```

> 复杂度分析

2 ^ 32 的数转化为26进制，次数不超过8次，时间复杂度O(1)

额外使用int来计算余数，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Excel Sheet Column Title.

Memory Usage: 38.7 MB, less than 16.05% of Java online submissions for Excel Sheet Column Title.
