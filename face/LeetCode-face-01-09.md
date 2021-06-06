### LeetCode-face-01-09

> 题目链接

[LeetCode-face-01-09](https://leetcode-cn.com/problems/string-rotation-lcci/)

> 思路

因为s1的头部拼接到尾部，形成s2，拼接s1和s1，再在字符串里面找s2

> 代码

```java
class Solution {
    public boolean isFlipedString(String s1, String s2) {
        return s1.length() == s2.length() && (s1 + s1).indexOf(s2) > -1;
    }
}
```

> 复杂度分析

遍历字符串搜索，时间复杂度O(m + n)

无额外使用其他常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了70.39%的用户
