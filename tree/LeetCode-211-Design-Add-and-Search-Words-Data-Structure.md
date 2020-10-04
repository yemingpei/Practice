### LeetCode-211-Design-Add-and-Search-Words-Data-Structure

> 题目链接

[LeetCode-211-Design-Add-and-Search-Words-Data-Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)

> 思路

字典树，思路同[LeetCode-208-Implement-Trie-Prefix-Tree](https://leetcode.com/problems/implement-trie-prefix-tree/)

> 代码

```java
class WordDictionary {
    class Trie{
        Trie child[];
        boolean isEnd;
        
        public Trie(){
            child = new Trie[26];
            isEnd = false;
        }
    }

    Trie root;
    public WordDictionary() {
        root = new Trie();
    }
    
    public void addWord(String word) {
        Trie curr = root;
        for(char c: word.toCharArray()){
            if(curr.child[c - 'a'] == null){
                curr.child[c -'a'] = new Trie();
            }
            curr = curr.child[c - 'a'];
        }
        curr.isEnd = true;
    }
    public boolean search(String word) {
        Trie curr = root;
        Queue<Trie> queue = new LinkedList<>();
        queue.add(curr);
        for(char c: word.toCharArray()){
            int size = queue.size();
            while(size-- > 0){
                curr = queue.poll();
                if(c == '.'){
                    for(int i=0; i< 26; i++){
                        if(curr.child[i] != null){
                            queue.add(curr.child[i]);
                        }
                    }
                }else{
                    if(curr.child[c - 'a'] != null){
                        queue.add(curr.child[c - 'a']);
                    }
                }
            }
        }
        while(!queue.isEmpty()){
            curr = queue.poll();
            if(curr.isEnd){
                return true;
            }
        }
        return false;
        
    }
}
```

> 复杂度分析

寻找前缀，时间复杂度O(m)

额外使用node数组用，空间复杂度O(n)

> 总结

Runtime: 44 ms, faster than 73.09% of Java online submissions for Design Add and Search Words Data Structure.

Memory Usage: 49.8 MB, less than 95.86% of Java online submissions for Design Add and Search Words Data Structure.
