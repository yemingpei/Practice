### LeetCode-face-01-04

> 题目链接

[LeetCode-face-01-04](https://leetcode-cn.com/problems/palindrome-permutation-lcci/)

> 思路

先统计各个字符的数量，如果字符串长度为1则可以有一个单数在最中间，其他必须为双数，才能是回文字符串

> 代码

```java
class Solution {
    public boolean canPermutePalindrome(String s) {
        boolean single = s.length() % 2 != 0;
        int[] result = new int[128];
        for(char c : s.toCharArray()){
            result[c]++;
        }
        int count = 0;
        for(int i : result){
            if(i % 2 != 0) count++;
        }
        return single ? count <= 1 : count == 0;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用一个boolean和一个int指针，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.4 MB, 在所有 Java 提交中击败了18.03%的用户
