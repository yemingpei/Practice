### LeetCode-318-Maximum-Product-of-Word-Lengths

> 题目链接

[LeetCode-318-Maximum-Product-of-Word-Lengths](https://leetcode.com/problems/maximum-product-of-word-lengths/)

> 思路

先把字符串转换成二进制，二进制0到25代表26个字母哪个存在的标记，比较这两个二进制就知道两个字符串是否有重复

> 代码

```java
class Solution {
    public int maxProduct(String[] words) {
        int n = words.length;
        int[] masks = new int[n];
        int[] lens = new int[n];
        int bitmask = 0;
        for (int i = 0; i < n; i++) {
          bitmask = 0;
          for (char ch : words[i].toCharArray()) {
            bitmask |= 1 << (ch - 'a');
          }
          masks[i] = bitmask;
          lens[i] = words[i].length();
        }
        int maxVal = 0;
        for (int i = 0; i < n; ++i)
          for (int j = i + 1; j < n; ++j)
            if ((masks[i] & masks[j]) == 0)
              maxVal = Math.max(maxVal, lens[i] * lens[j]);
        return maxVal;
    }
}
```

> 复杂度分析

徐娅遍历两重数组，时间复杂度O(n ^ 2)

额外使用数组变量，空间复杂度O(n)

> 总结

Runtime: 6 ms, faster than 99.64% of Java online submissions for Maximum Product of Word Lengths.

Memory Usage: 38.9 MB, less than 89.33% of Java online submissions for Maximum Product of Word Lengths.
