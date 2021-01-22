### LeetCode-388-Longest-Absolute-File-Path

> 题目链接

[LeetCode-388-Longest-Absolute-File-Pat](https://leetcode.com/problems/longest-absolute-file-path/)

> 思路

先用"\n"分割文件，通过\t来计算层级，使用.作为文件后缀的判断，更新最大长度

> 代码

```java
class Solution {
    public int lengthLongestPath(String input) {
        if (input.length() == 0)  return 0;
        int res = 0;
        int[] sum = new int[input.length() + 1];
        for (String s : input.split("\n")) {
            int level = s.lastIndexOf('\t') + 2;
            int len = s.length() - (level - 1);
            if (s.contains(".")) {
                res = Math.max(res, sum[level - 1] + len);
            } else {
                sum[level] = sum[level - 1] + len + 1;
            }
        }
        return res;
    }
}
```

> 复杂度分析

循环遍历input，时间复杂度O(n)

额外使用int数组保存结果，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Longest Absolute File Path.

Memory Usage: 36.7 MB, less than 91.07% of Java online submissions for Longest Absolute File Path.
