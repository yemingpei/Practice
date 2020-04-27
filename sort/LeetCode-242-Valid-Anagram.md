### LeetCode-242-Valid-Anagram

> 题目链接

[LeetCode-242-Valid-Anagram](https://leetcode.com/problems/valid-anagram/)

> 思路

记录每个字母的个数，核对字幕的个数是否相同

> 代码

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] count = new int[26];
        for (char c : s.toCharArray())
          count[c - 'a']++;
        for (char c : t.toCharArray())
          count[c - 'a']--;
        for (int j : count) {
          if (j != 0) return false;
        }
        return true;
    }
}
```

> 复杂度分析

循环遍历了一遍s字符串，再遍历t字符串，最后寻找count数组长度，用时2n+26，时间复杂度O(n)

额外使用26长度的int数组,空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 75.57% of Java online submissions for Valid Anagram.
Memory Usage: 41.5 MB, less than 5.16% of Java online submissions for Valid Anagram.
