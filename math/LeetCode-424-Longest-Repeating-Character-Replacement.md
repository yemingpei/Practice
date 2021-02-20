### LeetCode-424-Longest-Repeating-Character-Replacement

> 题目链接

[LeetCode-424-Longest-Repeating-Character-Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

> 思路

左右指针形成窗口，不大于maxFreq + k，来寻找最大的连续子串

> 代码

```java
class Solution {
    public int characterReplacement(String s, int k) {
        if (s.length() <= 1) return s.length();
        int result = 0;
        int len = s.length();
        int i = 0, j = 0, maxFreq = 0;
        int[] record = new int[26];
        while (j < len) {
            char cur = s.charAt(j);
            record[cur - 'A']++;
            maxFreq = Math.max(maxFreq, record[cur - 'A']);
            while ((maxFreq + k) < (j - i + 1)) {
                char tail = s.charAt(i);
                record[tail - 'A']--;
                i++;
            }
            result = Math.max(result, (j - i + 1));
            j++;
        }
        return result;
    }
}
```

> 复杂度分析

双指针遍历字符串，时间复杂度O(n)

额外使用26数组，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 95.45% of Java online submissions for Longest Repeating Character Replacement.

Memory Usage: 39.8 MB, less than 14.35% of Java online submissions for Longest Repeating Character Replacement.
