### LeetCode-521-longest-uncommon-subsequence-i

> 题目链接

[LeetCode-521-longest-uncommon-subsequence-i](https://leetcode-cn.com/problems/longest-uncommon-subsequence-i/)

> 思路

比较两个字符串是否一致，然后就输出较长的字符串

> 代码

```java
class Solution {
    public int findLUSlength(String a, String b) {
        if(a.equals(b)) return -1;
        return Math.max(a.length(), b.length());
    }
}
```

> 复杂度分析

比较两个字符串，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36 MB, 在所有 Java 提交中击败了83.03%的用户
