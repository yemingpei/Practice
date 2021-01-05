### LeetCode-392-Is-Subsequence

> 题目链接

[LeetCode-392-Is-Subsequence](https://leetcode.com/problems/is-subsequence/)

> 思路

逐个提取字符串，然后找到长串的位置，下次就从这个位置继续进行，没有找到则提前返回

> 代码

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int position = -1;
        for(char c : s.toCharArray()){
            position = t.indexOf(c, position + 1);
            if(position == -1) return false;
        }
        return true;
    }
}
```

> 复杂度分析

遍历两个字符串，时间复杂度O(m + n)

额外使用int来表示遍历的位置，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Is Subsequence.

Memory Usage: 36.7 MB, less than 94.07% of Java online submissions for Is Subsequence.
