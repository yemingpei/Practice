### LeetCode-224-Basic-Calculator

> 题目链接

[LeetCode-224-Basic-Calculator](https://leetcode.com/problems/basic-calculator/)

> 思路

逆波兰表达式，利用栈记录符号，实现等式计算

> 代码

```java
class Solution {
    public int calculate(String s) {
        if(s == null || s.length() < 1) return 0;
        int res = 0, curr = 0,sign = 1;
        Stack<Integer> stack = new Stack();
        for(char ch:s.toCharArray())
        {
            if(ch >= '0' && ch <= '9')
                curr=curr * 10 + (ch - '0');
            else if(ch == '+'||ch == '-'){
                res+=sign * curr;
                sign = ch == '+' ? 1:-1;
                curr = 0;
            }else if(ch == '('){
                stack.push(res);
                stack.push(sign);
                res = 0;
                sign = 1;
            }else if(ch == ')'){
                res+=sign * curr;
                int prevSign = stack.pop();
                res*=prevSign;
                res+=stack.pop();
                curr=0;
            }
        }
        return res + (sign * curr);
    }
}
```

> 复杂度分析

时间复杂度，时间复杂度O(n)

额外使用了栈，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 97.55% of Java online submissions for Basic Calculator.

Memory Usage: 38.8 MB, less than 99.47% of Java online submissions for Basic Calculator.
