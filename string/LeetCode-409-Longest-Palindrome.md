### LeetCode-409-Longest-Palindrome

> 题目链接

[LeetCode-409-Longest-Palindrome](https://leetcode.com/problems/longest-palindrome/)

> 思路

先统计每个字符的个数，然后单数的，要剔除一个，因为根据回文字符串的对称性，单数只能放在最中间有且只能有一个，所以count - singular + 1为由单数字符的最长返回值

> 代码

```java
class Solution {
    public int longestPalindrome(String s) {
        int[] result = new int[128];
        for(char ch: s.toCharArray()){
            result[ch - 'A']++;
        }
        int singular = 0;
        int count = 0;
        for(int i = 0; i < result.length; i++){
            if(result[i] % 2 == 1) singular++;
            count += result[i];
        }
        return singular == 0? count: count - singular + 1;
    }
}
```

> 复杂度分析

循环遍历字符串，时间复杂度O(n)

额外使用128长度的数组保存计数结果，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Longest Palindrome.

Memory Usage: 38.3 MB, less than 34.78% of Java online submissions for Longest Palindrome.
