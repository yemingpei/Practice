### LeetCode-139-Word-Break

> 题目链接

[LeetCode-139-Word-Break](https://leetcode.com/problems/word-break/)

> 思路

HashMap记录部分结果，避免重复计算，逐一匹配字符串是否吻合

> 代码

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        Map<Integer, Boolean> map = new HashMap<>();
        return checkWord(s, wordDict, 0, s.length(), map);
    }
    public boolean checkWord(String s, List<String> wordDict, int position, int max, Map<Integer, Boolean> map){
        if(map.containsKey(position)) return map.get(position);
        for(String word: wordDict){
            if(s.startsWith(word)){
                int flag = position + word.length();
                if(flag == max || checkWord(s.substring(word.length()), wordDict, flag, max, map)){
                    map.put(position, true);
                    return true;
                }
            }
        }
        map.put(position, false);
        return false;
    }
}
```

> 复杂度分析

递归匹配字符串，时间复杂度O(n ^ 2)

额外使用了HashMap<Integer, Boolean>,空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.47% of Java online submissions for Word Break.

Memory Usage: 38.9 MB, less than 93.57% of Java online submissions for Word Break.
