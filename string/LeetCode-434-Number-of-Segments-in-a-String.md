### LeetCode-434-Number-of-Segments-in-a-String

> 题目链接

[LeetCode-434-Number-of-Segments-in-a-String](https://leetcode.com/problems/number-of-segments-in-a-string/)

> 思路

遍历字符串，然后统计有多少个单词

> 代码

```java
class Solution {
    public int countSegments(String s) {
        int count = 0;
        for(int i = 0; i < s.length(); i++){
            if ((i == 0 || s.charAt(i-1) == ' ') && s.charAt(i) != ' ') 
               count++;
        }
        return count;
    }
}
```

> 复杂度分析

遍历了一遍字符串的每个字符，时间复杂度O(n)

无额外使用变量值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Number of Segments in a String.

Memory Usage: 38.6 MB, less than 5.85% of Java online submissions for Number of Segments in a String.
