### LeetCode-227-Basic-Calculator-II

> 题目链接

[LeetCode-227-Basic-Calculator-II](https://leetcode.com/problems/basic-calculator-ii/)

> 思路

遇到*和/就把栈顶的数取出来计算然后再入栈，遇到+和-就入栈，最后遍历栈取和

> 代码

```java
class Solution {
    public int calculate(String s) {
        s = s.trim();
        return core(s.toCharArray());
    }
    private int i = 0;
    private int core(char[] chs){
        Stack<Integer> stack = new Stack<>();
        int num = 0;
        char operation = '+';
        for (; i < chs.length; i++) {
            if(chs[i]==' '){
                continue;
            }
            if (Character.isDigit(chs[i])) {
                num = num * 10 + (chs[i] - '0');
            }
            if (!Character.isDigit(chs[i]) || i >= chs.length - 1) {
                if (operation == '+') {
                    stack.push(num);
                } else if (operation == '-') {
                    stack.push(-num);
                } else if (operation == '*') {
                    int a = stack.pop();
                    stack.push(a * num);
                } else if (operation == '/') {
                    int a = stack.pop();
                    stack.push(a / num);
                }
                if(i>=chs.length-1){
                    break;
                }
                operation = chs[i];
                num = 0;
            }
        }
        int sum = 0;
        while (!stack.isEmpty()) {
            sum += stack.pop();
        }
        return sum;
    }
}
```

> 复杂度分析

递归遍历了一遍字符串和栈，时间复杂度O(n + m)

额外使用一个栈辅助，空间复杂度O(m)

> 总结

Runtime: 9 ms, faster than 75.48% of Java online submissions for Basic Calculator II.

Memory Usage: 39 MB, less than 5.13% of Java online submissions for Basic Calculator II.
