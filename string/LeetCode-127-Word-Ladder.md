### LeetCode-127-Word-Ladder

> 题目链接

[LeetCode-127-Word-Ladder](https://leetcode.com/problems/word-ladder/)

> 思路

广度优先搜索，寻找可转化的最短路径，需要记录，每个单词可转化的下一个单词，存在Set<String>中，然后再递归，寻找转化的过程

> 代码

```java
class Solution {
    private Set<String> dictionary = new HashSet<>(); 
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        if (wordList == null || wordList.size() == 0) return 0;
        Set<String> start = new HashSet<>();
        Set<String> end = new HashSet<>();
        dictionary.addAll(wordList);
        start.add(beginWord);
        end.add(endWord);
        if (!dictionary.contains(endWord)) return 0;
        return bfs(start, end, 2);
    }

    public int bfs(Set<String> start, Set<String> end, int steps) {
        if (start.size() == 0) return 0;
        if (start.size() > end.size()) return bfs(end, start, steps);
        dictionary.removeAll(start);
        Set<String> next = new HashSet<>();
        for (String s : start) {
            char[] arr = s.toCharArray();
            for (int i = 0; i < arr.length; i++) {
                char tmp = arr[i];
                for (char c = 'a'; c <= 'z'; c++) {
                    if (tmp == c) continue;
                    arr[i] = c;
                    String nextWord = new String(arr);
                    if (dictionary.contains(nextWord)) {
                        if (end.contains(nextWord)) return steps;
                        else next.add(nextWord);
                    }
                }
                arr[i] = tmp;
            }
        }
        return bfs(next, end, steps + 1);
    }
}
```

> 复杂度分析

广度搜索，时间复杂度O(n ^ 2 * M)

额外使用set来记录单词的下一个转化，空间复杂度O(n)

> 总结

Runtime: 9 ms, faster than 99.67% of Java online submissions for Word Ladder.

Memory Usage: 40.6 MB, less than 87.39% of Java online submissions for Word Ladder.
