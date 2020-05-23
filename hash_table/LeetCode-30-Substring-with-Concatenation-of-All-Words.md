### LeetCode-30-Substring-with-Concatenation-of-All-Words

> 题目链接

[LeetCode-30-Substring-with-Concatenation-of-All-Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

> 思路
```java
{"abc" , "bcd"} String  =  “abcdabcefjkl” 比如abc符合，dab不符合，则直接跳到cef开始
```
先记录words的个数，排除重复的字符串，保证要检查的字串不同，然后开始遍历数组，遇到不匹配就直接跳过，从后面开始，详细见上面的例子，然后从第二个开始遍历，
共需要一个单词的长度次循环

> 代码

```java
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        List<Integer> result = new ArrayList<>();
        if (s == null || words == null || words.length == 0)return result;
        int size = s.length();
        int number = words.length;
        int length = words[0].length();
        if (s.length() < number * length) return result;
        HashMap<String, Integer> wordMap = new HashMap<>();
        for (String str: words)
            wordMap.put(str, wordMap.getOrDefault(str, 0) + 1);
        int right = size - number * length + 1;
        for (int i = 0; i < length; i++)
            for (int left = i; left < right; left += length) { 
                HashMap<String, Integer> recordMap = new HashMap<>();
                for (int j = number - 1; j > -1; j--) {
                    int id = left + j * length;
                    String subWord = s.substring(id, id + length);
                    int count = recordMap.getOrDefault(subWord, 0) + 1;
                    if (count > wordMap.getOrDefault(subWord, 0)) { 
                        left = id;  
                        break;
                    }
                    recordMap.put(subWord, count); 
                    if (j == 0)result.add(left);
                }
           }
        return result;
    }
}
```

> 复杂度分析

循环了m边数组，m为word的长度，时间复杂度O(nm)

额外使用了HashMap，List来辅助数据保存，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 99.76% of Java online submissions for Substring with Concatenation of All Words.

Memory Usage: 39.2 MB, less than 95.24% of Java online submissions for Substring with Concatenation of All Words.
