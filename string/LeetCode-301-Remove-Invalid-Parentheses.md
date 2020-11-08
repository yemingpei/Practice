### LeetCode-301-Remove-Invalid-Parentheses

> 题目链接

[LeetCode-301-Remove-Invalid-Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/)

> 思路

暴力法，寻找左右能闭合的组成需要的字串

> 代码

```java
class Solution {
    List<String> ans;
    public List<String> removeInvalidParentheses(String s) {
        ans = new ArrayList<>();
        helper(0, 0, s.toCharArray(), '(', ')');
        return ans;
    }
    public void helper(int last_i, int last_j, char[] s, char ch1, char ch2) {
        int cnt = 0;
        for (int i = last_i; i < s.length; i++) {
            if (s[i] == ch1) {
                cnt++;
            } else if (s[i] == ch2) {
                cnt--;
            }
            if (cnt < 0) {
                for (int j = last_j; j <= i; ++j) {
                    if (s[j] == ch2 && (j == last_j || s[j-1] != ch2)) {
                        char[] newS = deleteFromStr(s, j);
                        helper(i, j, newS, ch1, ch2);
                    }
                }
                return;
            }
        }
        int n = s.length;
        char[] newS = new char[n];
        n--;
        for (int i = 0; i < s.length; i++, n--) {
            newS[n] = s[i];
        }
        if (ch1 == '(') {
            helper(0, 0, newS, ch2, ch1);
        } else {
            ans.add(new String(newS));
        }
    }
    public char[] deleteFromStr(char[] s, int del) {
        int n = s.length;
        char[] newS = new char[n - 1];
        int j = 0;
        for (int i = 0; i < n; i++) {
            if (i != del) newS[j++] = s[i];
        }
        
        return newS;
    }   
}
```

> 复杂度分析

每个字符有取或者不取，两个选择，时间复杂度O(2 * n)

额外使用数组临时字串，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.83% of Java online submissions for Remove Invalid Parentheses.

Memory Usage: 37.8 MB, less than 5.51% of Java online submissions for Remove Invalid Parentheses.
