### LeetCode-140-Word-Break-II

> 题目链接

[LeetCode-140-Word-Break-II](https://leetcode.com/problems/word-break-ii/)

> 思路

HashMap记录部分结果，避免重复计算，逐一匹配字符串是否吻合

> 代码

```java
class Solution {
    public List<String> wordBreak(String s, List<String> wordDict) {
        Map<Integer, List<String>> hashMap = new HashMap<>();
        return findWord(s, wordDict, 0, hashMap, s.length());
    }
    public List<String> findWord(String s, List<String> wordDict, int start, Map<Integer,List<String>> hashMap, int max){
        if(hashMap.containsKey(start)) {
            return hashMap.get(start);
        }
        List<String> list = new ArrayList<>();
        for(String str : wordDict){
            if(s.startsWith(str)){
                int position = start + str.length();
                if(position == max){
                    list.add(str);
                }else{
                    List<String> subList = findWord(s.substring(str.length()), wordDict, position, hashMap, max);
                    for(String sub : subList){
                        list.add(str + " " + sub);
                    }
                }
            }
        }
        hashMap.put(start, list);
        return list;
    }
}
```

> 复杂度分析

递归匹配字符串，时间复杂度O(n ^ 3)

额外使用了HashMap<Integer, List<String>>,空间复杂度O(n ^ 2)

> 总结

Runtime: 7 ms, faster than 79.44% of Java online submissions for Word Break II.

Memory Usage: 39.3 MB, less than 97.22% of Java online submissions for Word Break II.
