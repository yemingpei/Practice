### LeetCode-423-Reconstruct-Original-Digits-from-English

> 题目链接

[LeetCode-423-Reconstruct-Original-Digits-from-English](https://leetcode.com/problems/reconstruct-original-digits-from-english/)

> 思路

先用z,w,x,g来确定0，2，6，8的个数，减去o,r,h,s的数量，再用h,s确定3，7，减去r,n的数量，用r确定4，减去o,f的数量,最后用o,f,n确定1，5，9

> 代码

```java
class Solution {
    public String originalDigits(String s) {
        int[] digits = new int[26];
        for(char a : s.toCharArray()){
            digits[a - 'a']++;
        }
        int[] result = new int[10];
        result[0] = digits['z' - 'a'];
        digits['r' - 'a'] -= result[0];
        digits['o' - 'a'] -= result[0];
        result[2] = digits['w' - 'a'];
        digits['o' - 'a'] -= result[2];
        result[6] = digits['x' - 'a'];
        digits['s' - 'a'] -= result[6];
        result[8] = digits['g' - 'a'];
        digits['h' - 'a'] -= result[8];
        result[3] = digits['h' - 'a'];
        digits['r' - 'a'] -= result[3];
        result[4] = digits['r' - 'a'];
        digits['f' - 'a'] -= result[4];
        digits['o' - 'a'] -= result[4];
        result[7] = digits['s' - 'a'];
        digits['n' - 'a'] -= result[7];
        result[1] = digits['o' - 'a'];
        digits['n' - 'a'] -= result[1];
        result[5] = digits['f' - 'a'];
        result[9] = digits['n' - 'a'] / 2;
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i< result.length; i++){
            for(int j = 0; j < result[i]; j++)
                sb.append(i);
        }
        return sb.toString();
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用26和10长度的数组，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Reconstruct Original Digits from English.

Memory Usage: 40 MB, less than 23.81% of Java online submissions for Reconstruct Original Digits from English.
