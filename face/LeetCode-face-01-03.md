### LeetCode-face-01-03

> 题目链接

[LeetCode-face-01-03](https://leetcode-cn.com/problems/string-to-url-lcci/)

> 思路

直接拼接字符串，遇到空格就转换成%20

> 代码

```java
class Solution {
    public String replaceSpaces(String S, int length) {
        char[] chars = S.toCharArray();
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < length; i++){
            if(chars[i] == ' ') sb.append("%20");
            else sb.append(chars[i]);
        }
        return sb.toString();
    }
}
```

> 复杂度分析

遍历了字符串，时间复杂度O(n)

额外使用char数组，空间复杂度O(n)

> 总结

执行用时：18 ms, 在所有 Java 提交中击败了45.47%的用户

内存消耗：47.2 MB, 在所有 Java 提交中击败了18.98%的用户
