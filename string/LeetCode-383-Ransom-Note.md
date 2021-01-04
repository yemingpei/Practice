### LeetCode-383-Ransom-Note

> 题目链接

[LeetCode-383-Ransom-Note](https://leetcode.com/problems/ransom-note/)

> 思路

先保存次字符串的字符个数，然后用第一个去减，无法减则证明后者不能生成前者

> 代码

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] letters = new int[26];
        for(int i = 0; i < magazine.length(); i++){
            letters[magazine.charAt(i) - 'a']++;
        }
        for(int i = 0; i < ransomNote.length(); i++){
            if(letters[ransomNote.charAt(i) - 'a'] == 0) return false;
            letters[ransomNote.charAt(i) - 'a']--;
        }
        return true;
    }
}
```

> 复杂度分析

遍历两个字符串，时间复杂度O(n + m)

需要长度为26的数组来保存结果，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 78.01% of Java online submissions for Ransom Note.

Memory Usage: 39.1 MB, less than 83.31% of Java online submissions for Ransom Note.
