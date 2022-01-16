### LeetCode-639-decode-ways-ii

> 题目链接

[LeetCode-639-decode-ways-ii](https://leetcode-cn.com/problems/decode-ways-ii/)

> 思路

动态规划，新加的这个字符和前文的关系

> 代码

```java
class Solution {
    private int MOD = (int) (1e9 + 7);

    public int numDecodings(String s) {
        int n = s.length();
        long a = 0, b = 1;
        int pre = 0;
        long c = 0;
        int mi = 1000000007;
        char x = '0';
        for (int i = 0; i < n; i++) {
            int ki = s.charAt(i) - x;
            c = 0;
            if (ki == 0 && (pre > 2)) {
                return 0;
            }
            if (ki != 0) {
                if (ki < 0) {
                    c += 9 * b;
                } else {
                    c += b;
                }
            }
            if (pre < 0) {
                if (ki < 0) {
                    c += 15 * a;
                } else if (ki <= 6) {
                    c += 2 * a;
                } else {
                    c += a;
                }
            } else {
                if (pre == 1) {
                    if (ki < 0) {
                        c += 9 * a;
                    } else {
                        c += a;
                    }
                } else if (pre == 2) {
                    if (ki < 0) {
                        c += 6 * a;
                    } else if (ki <= 6) {
                        c += a;
                    }
                }
            }
            c = c % mi;
            a = b;
            b = c;
            pre = ki;
        }
        return (int) c;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了98.97%的用户
