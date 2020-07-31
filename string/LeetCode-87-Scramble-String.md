### LeetCode-87-Scramble-String

> 题目链接

[LeetCode-87-Scramble-String](https://leetcode.com/problems/scramble-string/)

> 思路

先比较字符串个数，然后比较前后部分是否是交换关系，不断递归完成，不符合规则就提前return

> 代码

```java
class Solution {
    public boolean isScramble(String s1, String s2) {
       if(s1.equals(s2))
         return true;
       int s1Array[] = new int[26];
       int s2Array[] = new int[26];
       for(int i = 0; i < s1.length(); i++) {
          s1Array[s1.charAt(i) - 'a']++;
          s2Array[s2.charAt(i) - 'a']++;
       }
       for(int i = 0; i < 26; i++)
         if(s1Array[i] != s2Array[i])
            return false;
       for(int i = 1; i < s1.length(); i++) {
         if( isScramble(s1.substring(0, i), s2.substring(0, i))
            && isScramble(s1.substring(i), s2.substring(i)) )
            return true;
         if( isScramble(s1.substring(0, i), s2.substring(s1.length() - i))
            && isScramble(s1.substring(i), s2.substring(0, s1.length() - i)))
            return true;
       }
       return false;
    }
}
```

> 复杂度分析

暴力比较法，不断递归寻找是不是相同的字串 ，时间复杂度O(n ^ 4)

递归，不断创建26长度的数组，空间复杂度O(n ^ 3)

> 总结

Runtime: 2 ms, faster than 95.23% of Java online submissions for Scramble String.

Memory Usage: 39.6 MB, less than 34.78% of Java online submissions for Scramble String.
