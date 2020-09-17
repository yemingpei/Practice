### LeetCode-214-Shortest-Palindrome

> 题目链接

[LeetCode-214-Shortest-Palindrome](https://leetcode.com/problems/shortest-palindrome/)

> 思路

用KMP算法寻找回文字符串，寻找到相同的部分，就还需要另外一个方向，继续寻找，校验，最后完成拼接。

> 代码

```java
class Solution {
    public String shortestPalindrome(String s) {
        int n = s.length();
        if(n == 0) return s;
        int[] fail = new int[n];
        fail[0] = -1;
        for (int i = 1; i < n; ++i) {
            int j = fail[i - 1];
            while (j != -1 && s.charAt(j + 1) != s.charAt(i)) {
                j = fail[j];
            }
            if (s.charAt(j + 1) == s.charAt(i)) {
                fail[i] = j + 1;
            }
        }
        int best = -1;
        for (int i = n - 1; i >= 0; --i) {
            while (best != -1 && s.charAt(best + 1) != s.charAt(i)) {
                best = fail[best];
            }
            if (s.charAt(best + 1) == s.charAt(i)) {
                ++best;
            }
        }
        String add = (best == n - 1 ? "" : s.substring(best + 1));
        StringBuffer ans = new StringBuffer(add).reverse();
        ans.append(s);
        return ans.toString();
    }
}
```

> 复杂度分析

KMP算法检验回文 ，时间复杂度O(n)

需要next数组协助，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 91.26% of Java online submissions for Shortest Palindrome.

Memory Usage: 39.5 MB, less than 79.00% of Java online submissions for Shortest Palindrome.
