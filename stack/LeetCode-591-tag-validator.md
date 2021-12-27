### LeetCode-591-tag-validator

> 题目链接

[LeetCode-591-tag-validator](https://leetcode-cn.com/problems/tag-validator/)

> 思路

检索左右括号一样的原理，需要检查标签的正确性

> 代码

```java
class Solution {
    public boolean isValid(String code) {
        Deque<String> stack = new LinkedList<>();
        boolean root = false;
        for (int i = 0; i < code.length(); i++) {
            if (i > 0 && stack.isEmpty()) return false;
            if (code.startsWith("<![CDATA[", i)) {
                int j = i + 9;
                i = code.indexOf("]]>", j);
                if (i < 0) return false;
                i += 2;
            } else if (code.startsWith("</", i)) {
                int j = i + 2;
                i = code.indexOf(">", j + 1);
                if (i < 0 || i - j > 9) return false;
                if (stack.isEmpty() || !stack.pop().equals(code.substring(j, i))) return false;
                root = true;
            } else if (code.startsWith("<", i)) {
                int j = i + 1;
                i = code.indexOf(">", j + 1);
                if (i < 0 || i - j > 9) return false;
                for (int k = j; k < i; k++) {
                    if (!Character.isUpperCase(code.charAt(k))) return false;
                }
                stack.push(code.substring(j, i));
            }
        }
        return stack.isEmpty() && root;
    }
}
```

> 复杂度分析

进栈，出栈操作，时间复杂度O(n)

额外使用stack，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.5 MB, 在所有 Java 提交中击败了93.51%的用户
