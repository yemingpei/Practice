### LeetCode-282-Expression-Add-Operators

> 题目链接

[LeetCode-282-Expression-Add-Operators](https://leetcode.com/problems/expression-add-operators/)

> 思路

深度遍历，不断递归，分裂不同的结果，暴力推进

> 代码

```java
class Solution {
    public List<String> addOperators(String num, int target) {
        List<String> res = new LinkedList<>();
        if(num.length()==0||Long.valueOf(num)>Integer.MAX_VALUE)
            return res;
        char[] path = new char[num.length() * 2 - 1];
        char[] digits = num.toCharArray();
        long n = 0;
        for (int i = 0; i < digits.length; i++) {
            n = n * 10 + digits[i] - '0';
            path[i] = digits[i];
            dfs(res,path, i+1, 0, n, digits, i+1, target);
            if(n==0) break;
        }
        return res;
    }
    
    public void dfs(List<String> ret, char[] path, int len, long left, long cur, char[] digits, int pos, int target) {
        if (pos == digits.length) {
            if (left + cur == target) ret.add(new String(path, 0, len));
            return;
        }
        long n = 0;
        int j = len + 1;
        for (int i = pos; i < digits.length; i++) {
            n = n * 10 + digits[i] - '0';
            path[j++] = digits[i];
            path[len] = '+';
            dfs(ret, path, j, left + cur, n, digits, i + 1, target);
            path[len] = '-';
            dfs(ret, path, j, left + cur, -n, digits, i + 1, target);
            path[len] = '*';
            dfs(ret, path, j, left, cur * n, digits, i + 1, target);
            if (digits[pos] == '0') break; 
        }
     }
}
```

> 复杂度分析

每个符号最多有四个可能，时间复杂度O(4 ^ m)

额外使用char数组，空间复杂度O(m)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Expression Add Operators.

Memory Usage: 39.3 MB, less than 5.42% of Java online submissions for Expression Add Operators.
