### LeetCode-522-longest-uncommon-subsequence-ii

> 题目链接

[LeetCode-522-longest-uncommon-subsequence-ii](https://leetcode-cn.com/problems/longest-uncommon-subsequence-ii/)

> 思路

先排序，然后依次比较是否为最小子序列

> 代码

```java
class Solution {
    public boolean isSubsequence(String x, String y) {
        int j = 0;
        for (int i = 0; i < y.length() && j < x.length(); i++)
            if (x.charAt(j) == y.charAt(i))
                j++;
        return j == x.length();
    }
    public int findLUSlength(String[] strs) {
        Arrays.sort(strs, new Comparator < String > () {
            public int compare(String s1, String s2) {
                return s2.length() - s1.length();
            }
        });
        for (int i = 0, j; i < strs.length; i++) {
            boolean flag = true;
            for (j = 0; j < strs.length; j++) {
                if (i == j)
                    continue;
                if (isSubsequence(strs[i], strs[j])) {
                    flag = false;
                    break;
                }
            }
            if (flag)
                return strs[i].length();
        }
        return -1;
    }
}
```

> 复杂度分析

比较两个字符串，时间复杂度O(x * n ^ 2)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.55%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了53.18%的用户
