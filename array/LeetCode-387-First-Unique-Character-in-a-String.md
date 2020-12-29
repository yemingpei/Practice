### LeetCode-387-First-Unique-Character-in-a-String

> 题目链接

[LeetCode-387-First-Unique-Character-in-a-String](https://leetcode.com/problems/first-unique-character-in-a-string/)

> 思路

先遍历字符串，记录字符的个数，然后再遍历字符串，返回首个不重复的位置

> 代码

```java
class Solution {
    public int firstUniqChar(String s) {
        int[] chars = new int[26];
        for(char ch : s.toCharArray()){
            chars[ch-'a'] = chars[ch - 'a'] + 1;
        }
        for(int i = 0; i < s.length(); i++){
            if(chars[s.charAt(i) - 'a'] == 1)
               return i;
        }
        return -1;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要长度26的数组保存计数，空间复杂度O(1)

> 总结

Runtime: 5 ms, faster than 95.93% of Java online submissions for First Unique Character in a String.

Memory Usage: 39.7 MB, less than 28.03% of Java online submissions for First Unique Character in a String.
