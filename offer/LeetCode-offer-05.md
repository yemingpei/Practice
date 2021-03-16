### LeetCode-offer-05

> 题目链接

[LeetCode-offer-05](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

> 思路

遍历字符串，遇到空格就置换成%20，否则就拼接原来的字符

> 代码

```java
class Solution {
    public String replaceSpace(String s) {
        StringBuilder sb = new StringBuilder();
        for(char c : s.toCharArray()){
            if(c == ' ') sb.append("%20"); 
            else sb.append(c);
        }
        return sb.toString();
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用StringBuilder，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.1 MB, 在所有 Java 提交中击败了84.19%的用户
