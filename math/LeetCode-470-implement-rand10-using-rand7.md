### LeetCode-470-implement-rand10-using-rand7

> 题目链接

[LeetCode-470-implement-rand10-using-rand7](https://leetcode-cn.com/problems/implement-rand10-using-rand7/)

> 思路

利用两次rand7，使用同概率的结果来代替rand10

> 代码

```java
class Solution extends SolBase {
    public int rand10() {
        int a, b, idx;
        while (true) {
            a = rand7();
            b = rand7();
            idx = b + (a - 1) * 7;
            if (idx <= 40) {
                return 1 + (idx - 1) % 10;
            }
            a = idx - 40;
            b = rand7();
            idx = b + (a - 1) * 7;
            if (idx <= 60) {
                return 1 + (idx - 1) % 10;
            }
            a = idx - 60;
            b = rand7();
            idx = b + (a - 1) * 7;
            if (idx <= 20) {
                return 1 + (idx - 1) % 10;
            }
        }
    }
}
```

> 复杂度分析

多次调用rand7，时间复杂度O(1)

额外使用int，空间复杂度O(1)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了58.59%的用户

内存消耗：43.4 MB, 在所有 Java 提交中击败了59.57%的用户
