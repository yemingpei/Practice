### LeetCode-face-16-26

> 题目链接

[LeetCode-face-16-26](https://leetcode-cn.com/problems/calculator-lcci/)

> 思路

用a和b保存计算的两个数，如果出现后面的运算符比前面的运算符优先级高，则使用递归

> 代码

```java
class Solution {
    public int calculate(String s) {
        char[] chars = s.toCharArray();
        return eval(chars, 0, chars.length);
    }

    private int eval(char[] chars, int s, int e){
        int a = 0;
        int b = 0;
        char op = '?';
        int mark = 0;
        for (int i = s; i < e; i++) {
            if (chars[i] == ' '){
                continue;
            }
            if (chars[i] >= '0' && chars[i] <='9') {
                if (op == '?') { 
                    a = a * 10 + (chars[i] - '0');
                } else {
                    b = b * 10 + (chars[i] - '0');
                }
            } else if (op == '?' && (chars[i] == '+' || chars[i] == '-')) {
                op = chars[i];
                mark = i + 1;
            } else if (op == '?' && (chars[i] == '*' || chars[i] == '/')) {
                op = chars[i];
            }else if (op!='?' && (chars[i] == '+' || chars[i] == '-' || chars[i] == '*' || chars[i] == '/')) {
                if (op == '+') {
                    if(chars[i] == '+' || chars[i] == '-'){
                        a = a + b;
                    } else {
                        return a + eval(chars, mark, e);
                    } 
                } else if (op == '-'){
                    if (a==0){
                        a = -b;
                    } else {
                        if (chars[i] == '+' || chars[i] == '-'){
                            a = a - b;
                        } else {
                            return a + eval(chars, mark-1, e);
                        } 
                    }
                } else if (op == '*'){
                    a = a * b;
                } else {
                    a = a / b;
                }
                op = chars[i];
                b = 0;
                mark = i + 1;
            }
        }
        if (op == '?') {
            return a;
        } else {
            if (op == '+') {
                return a + b;
            } else if (op == '-') {
                return a - b;
            } else if (op == '*') {
                return a * b;
            } else if (op == '/') {
                return a / b;
            }
        }
        return 0;
    }
}
```

> 复杂度分析

遍历一遍字符串，时间复杂度O(n)

额外使用递归，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了92.36%的用户
