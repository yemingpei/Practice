### LeetCode-126-Word-Ladder-II

> 题目链接

[LeetCode-126-Word-Ladder-II](https://leetcode.com/problems/word-ladder-ii/)

> 思路

广度优先搜索，寻找可转化的最短路径，需要记录，每个单词可转化的下一个单词，存在Map<String, List<String>>中，然后再回溯，寻找转化的过程

> 代码

```java
class Solution {
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        List<List<String>> result = new ArrayList<>();
        Set<String> dict = new HashSet<>(wordList);
        if(!dict.contains(endWord)) return result;
        Set<String> startSet = new HashSet<>();
        Set<String> endSet = new HashSet<>();
        startSet.add(beginWord);
        endSet.add(endWord);
        Map<String, List<String>> map = new HashMap<>();
        BFS(startSet, endSet, dict, map, false);  
        List<String> list = new ArrayList<>();
        list.add(beginWord);
        DFS(beginWord, endWord, result, list, map);
        return result;
    }
    private void BFS(Set<String> startSet, Set<String> endSet, Set<String> dict, Map<String, List<String>> map, boolean reverse){
        if(startSet.size() == 0) return;
        if(startSet.size() > endSet.size()){
            BFS(endSet, startSet, dict, map, !reverse);
            return;
        }
        boolean finish = false;
        Set<String> temp = new HashSet<>();
        dict.removeAll(startSet);  
        for(String s:startSet){
            char[] chars = s.toCharArray();
            for(int i=0; i<chars.length; i++){
                char cur = chars[i];
                for(char c ='a'; c<='z'; c++){
                    chars[i] = c;
                    String word = new String(chars);
                    if(dict.contains(word)){
                        if(endSet.contains(word)){
                            finish = true;
                        }else{
                            temp.add(word);
                        }
                        String key = reverse? word:s;
                        String val = reverse? s:word;
                        if(map.get(key) == null) map.put(key, new ArrayList<>());
                        map.get(key).add(val);
                    }
                }
                chars[i] = cur;
            }
        }
        if(!finish) BFS(temp, endSet, dict, map, reverse);
    }
    private void DFS(String beginWord, String endWord, List<List<String>> result, List<String> list, Map<String, List<String>> map){
        if(beginWord.equals(endWord)){
            result.add(new ArrayList<>(list));
            return;
        }
        if(map.get(beginWord) == null) return;
        for(String next:map.get(beginWord)){
            list.add(next);
            DFS(next, endWord, result, list, map);
            list.remove(list.size()-1);
        }
        return;
    }
}
```

> 复杂度分析

广度搜索，时间复杂度O(n ^ 2 * M)

额外使用Map来记录单词的下一个转化，空间复杂度O(n ^ 2)

> 总结

Runtime: 30 ms, faster than 91.88% of Java online submissions for Word Ladder II.

Memory Usage: 52.9 MB, less than 5.83% of Java online submissions for Word Ladder II.
