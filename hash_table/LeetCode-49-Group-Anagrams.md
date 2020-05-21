### LeetCode-49-Group-Anagrams

> 题目链接

[LeetCode-49-Group-Anagrams](https://leetcode.com/problems/group-anagrams/)

> 思路

遍历一遍数组，数值用HashMap来检索List，用26个计数器记录字符出现的个数

> 代码

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();
        for (String s : strs) {
          char[] count = new char[26];
          for (char element : s.toCharArray()) {
            count[element - 'a']++;
          }
          String key = new String(count);
          List<String> list = map.get(key);
          if (list == null) {
            list = new ArrayList<>();
            map.put(key, list);
            result.add(list);
          }
          list.add(s);
        }
        return result;
    }
}
```

> 复杂度分析

for循环遍历了一遍字符，用时n，再用26的记录组成key，时间复杂度O(n)

额外使用了HashMap，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 99.35% of Java online submissions for Group Anagrams.

Memory Usage: 43.4 MB, less than 68.42% of Java online submissions for Group Anagrams.
