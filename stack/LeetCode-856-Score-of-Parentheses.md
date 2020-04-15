### LeetCode-856-Score-of-Parentheses

> 题目链接

[LeetCode-856-Score-of-Parentheses](https://leetcode.com/problems/score-of-parentheses/)

> 思路

"()()"做加法，"(())"做乘法，利用栈，遇到"("就进栈，")"就出栈计算，分别写出加法和乘法的分支，得出最终的分数

> 代码

```java
class Solution {
    public int scoreOfParentheses(String S) {
        Stack<Integer> stack = new Stack<Integer>();
        char[] text = S.toCharArray();
        int result = 0;
        for (char a : text) {
          if (a == '(') {
            stack.push(result);
            result = 0;
          } else if (result == 0)
            result = stack.pop() + 1;
          else
            result = stack.pop() + result * 2;
        }
        return result;
    }
}
```

> 复杂度分析

遍历了一遍字符串长度的char数组，时间复杂度O(n)

额外使用了char数组,空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Score of Parentheses.
Memory Usage: 37.2 MB, less than 16.67% of Java online submissions for Score of Parentheses.
