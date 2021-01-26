### LeetCode-393-UTF-8-Validations

> 题目链接

[LeetCode-393-UTF-8-Validations](https://leetcode.com/problems/utf-8-validation/)

> 思路

每四位一个字节，位运算来过滤一部分的值，然后计算得到是否符合utf8

> 代码

```java
class Solution {
    public boolean validUtf8(int[] data) {
        return validUtf8(data, 0, data.length);
    }

    private boolean validUtf8(int[] data, int lo, int hi) {
        if (lo >= hi) return true;
        int cur = data[lo];
        int head = cur & 0xFF;
        int cnt = 0;
        while (true) {
            head <<= 1;
            if ((head & 0x100) == 0x100) cnt++;
            else break;
        }
        if (cnt == 1 || cnt > 4) return false;
        if (cnt == 0) return validUtf8(data, lo + 1, hi);
        int tmp = cur >> (7 - cnt);
        if (tmp % 2 == 0) {
            for (int i = 1; i < cnt; i++) {
                if (lo + i >= hi) return false;
                tmp = data[lo + i] >> 6;
                if (2 != tmp) {
                    return false;
                }
            }
        }
        return validUtf8(data, lo + cnt, hi);
    }
}
```

> 复杂度分析

循环遍历数组，时间复杂度O(n)

额外使用三个int变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 98.26% of Java online submissions for UTF-8 Validation.

Memory Usage: 45.3 MB, less than 5.22% of Java online submissions for UTF-8 Validation.
