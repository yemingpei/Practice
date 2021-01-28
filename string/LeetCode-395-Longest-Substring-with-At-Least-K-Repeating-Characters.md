### LeetCode-395-Longest-Substring-with-At-Least-K-Repeating-Characters

> 题目链接

[LeetCode-395-Longest-Substring-with-At-Least-K-Repeating-Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

> 思路

不断用次数不够k的字符来分割子字符串，得到出现次数大于等于k为止的最大长度。

> 代码

```java
class Solution {
    public int longestSubstring(String s, int k) {
        int res = 0;
        boolean[] m = new boolean[26];
        int[] mid = new int[26];
        for (int i = 0; i < s.length(); i++) {
            mid[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < mid.length; i++) {
            if (mid[i] < k) {
                m[i] = true;
            }
        }
        int start = 0;
        boolean f = true;
        for (int i = 0; i < s.length(); i++) {
            if (m[s.charAt(i) - 'a']) {
                f = false;
                if (start < i) {
                    res = Integer.max(res, longestSubstring(s.substring(start, i), k));
                }
                start = i + 1;
            }
        }
        if (f) {
            res = s.length();
        } else {
            if(start < s.length()) {
                res = Integer.max(res, longestSubstring(s.substring(start, s.length()), k));
            }
        }
        return res;
    }
}
```

> 复杂度分析

循环遍历数组，最多26次，时间复杂度O(n)

额外使用int长度26的数组变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Longest Substring with At Least K Repeating Characters.

Memory Usage: 37.1 MB, less than 68.54% of Java online submissions for Longest Substring with At Least K Repeating Characters.
