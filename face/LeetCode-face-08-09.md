### LeetCode-face-08-09

> 题目链接

[LeetCode-face-08-09](https://leetcode-cn.com/problems/bracket-lcci/)

> 思路

左右括号数量相等，必然选择'('，否则'('和')'做出选择

> 代码

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        parenthesis(result, n, new StringBuilder(), 0, 0);
        return result;
    }

    public void parenthesis(List<String> result, int n, StringBuilder text, int i, int j){
        if(i == n && j == n){
            result.add(text.toString());
            return;
        }
        if(i == j){
            text.append('(');
            parenthesis(result, n, text, i + 1, j);
            text.deleteCharAt(text.length() - 1);
        }else{
            if(i != n){
                text.append('(');
                parenthesis(result, n, text, i + 1, j);
                text.deleteCharAt(text.length() - 1);
            }
            text.append(')');
            parenthesis(result, n, text, i, j + 1);
            text.deleteCharAt(text.length() - 1);
        }
    }
}
```

> 复杂度分析

左右括号做出选择，时间复杂度O(2 ^ n) 

递归栈深度为2n，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了91.48%的用户
