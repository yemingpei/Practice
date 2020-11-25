### LeetCode-306-Additive-Number

> 题目链接

[LeetCode-306-Additive-Number](https://leetcode.com/problems/additive-number/)

> 思路

深度遍历法，不断寻找下一个数字和前两个的和比较，需要记住前一个数字和前两个的和，递归专心找下一个数字

> 代码

```java
class Solution {
    public boolean isAdditiveNumber(String num) {
        return dfs(num, num.length(), 0, 0, 0, 0);
    }
    private boolean dfs(String num, int len, int idx, long sum, long pre, int k) {
        if (idx == len) return k > 2;
        for (int i = idx; i < len; i++) {
            long cur = fetchCurValue(num, idx, i);
            if (cur < 0) continue;
            if (k >= 2 && cur != sum) continue;
            if (dfs(num, len, i + 1, pre + cur, cur, k + 1)) return true;
        }
        return false;
    }
    private long fetchCurValue(String num, int l, int r) {
        if (l < r && num.charAt(l) == '0') return -1;
        long res = 0;
        while (l <= r) {
            res = res * 10 + num.charAt(l++) - '0';
        }
        return res;
    }
}
```

> 复杂度分析

循环遍历两个字符串，时间复杂度O(n ^ 2)

额外使用int类型指定数字，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Additive Number.

Memory Usage: 36.6 MB, less than 96.76% of Java online submissions for Additive Number.
