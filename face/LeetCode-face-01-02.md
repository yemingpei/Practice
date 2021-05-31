### LeetCode-face-01-02

> 题目链接

[LeetCode-face-01-02](https://leetcode-cn.com/problems/check-permutation-lcci/)

> 思路

先计算字符出现的次数，然后遍历另一个字符串个数不同，则提前退出

> 代码

```java
class Solution {
    public boolean CheckPermutation(String s1, String s2) {
        if(s1.length() != s2.length()) return false;
        int[] count = new int[26];
        for(char c : s1.toCharArray()){
            count[c - 'a']++;
        }
        for(char c : s2.toCharArray()){
            count[c - 'a']--;
            if(count[c - 'a'] < 0) return false;
        }
        return true;
    }
}
```

> 复杂度分析

遍历了长度为n的字符串两次，时间复杂度O(n)

额外使用一个固定长度的数组，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了91.74%的用户
