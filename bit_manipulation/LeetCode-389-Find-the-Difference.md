### LeetCode-389-Find-the-Difference

> 题目链接

[LeetCode-389-Find-the-Difference](https://leetcode.com/problems/find-the-difference/)

> 思路

因为两个字符串只有一个是新增的字符，其他字符，个数都是偶数，所以可以使用位运算来求解，最后遍历完，剩下的就是要求的字符

> 代码

```java
class Solution {
    public char findTheDifference(String s, String t) {
        int result = 0;
        for(char ch: s.toCharArray()){
            result ^= ch;
        }
        for(char ch: t.toCharArray()){
            result ^= ch;
        }
        return (char)result;
    }
}
```

> 复杂度分析

位运算遍历两个字符串，时间复杂度O(n + m)

额外int来保存位运算的结果，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.09% of Java online submissions for Find the Difference.

Memory Usage: 37.6 MB, less than 49.39% of Java online submissions for Find the Difference.
