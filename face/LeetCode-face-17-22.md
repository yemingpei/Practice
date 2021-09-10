### LeetCode-face-17-22

> 题目链接

[LeetCode-face-17-22](https://leetcode-cn.com/problems/word-transformer-lcci/)

> 思路

深度搜索，用hashSet来保存访问过的字符串，用回溯法实现，剪枝提前退出

> 代码

```java
class Solution {
    public List<String> findLadders(String beginWord, String endWord, List<String> wordList) {
        HashSet<String> set = new HashSet<>(wordList);
        ArrayList<String> list = new ArrayList<>();
        HashSet<String> visited = new HashSet<>();
        list.add(beginWord);
        visited.add(beginWord);
        if(dfs(beginWord.toCharArray(), endWord, set, visited, list)) return list;
        return new ArrayList<>();
    }
    public boolean dfs(char[] word, String endWord, HashSet<String> set,HashSet<String> visited, ArrayList<String> list){
        if(endWord.equals(new String(word))){
            return true;
        }
        for(int i = 0; i < word.length; i++){
            char c = word[i];
            for(char j = 'a'; j <= 'z'; j++){
                word[i] = j;
                String s = new String(word);
                if(set.contains(s) && !visited.contains(s)){
                    visited.add(s);
                    list.add(s);
                    if(dfs(word, endWord, set, visited, list)){
                        return true;
                    }
                    list.remove(list.size()-1);
                }
            }
            word[i] = c;
        }
        return false;
    }
}
```

> 复杂度分析

最坏情况，需要遍历全部组合，时间复杂度O(n!)

额外使用hashSet变量辅助，空间复杂度O(n)

> 总结

执行用时：29 ms, 在所有 Java 提交中击败了96.21%的用户

内存消耗：41.1 MB, 在所有 Java 提交中击败了13.01%的用户
