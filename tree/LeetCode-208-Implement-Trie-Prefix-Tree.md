### LeetCode-208-Implement-Trie-Prefix-Tree

> 题目链接

[LeetCode-208-Implement-Trie-Prefix-Tree](https://leetcode.com/problems/implement-trie-prefix-tree/)

> 思路

不断寻找前缀

> 代码

```java
class Trie {

   class Node{
       
        Node [] children;
        boolean isEnd; 
       Node(){
           isEnd = false;
           children  = new Node[26]; 
       }
    }
    Node root; 
    /** Initialize your data structure here. */
    public Trie() {
        root = new Node(); 
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        Node cur = root; 
        for(int i = 0; i < word.length(); i++) {
            int index = word.charAt(i) - 'a'; 
            if(cur.children[index] == null) {
                cur.children[index] = new Node(); 
            }
            cur = cur.children[index]; 
        }
        cur.isEnd  = true; 
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        Node cur = root; 
        for(int i = 0; i < word.length(); i++) {
            int index = word.charAt(i) - 'a'; 
            if(cur.children[index] == null)
                return false; 
            else 
                cur = cur.children[index];
        }
        return cur != null && cur.isEnd; 
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
         Node cur = root; 
        for(int i = 0; i < prefix.length(); i++) {
            int index = prefix.charAt(i) - 'a'; 
            if(cur.children[index] == null)
                return false; 
            else 
                cur = cur.children[index];
        }
        return cur != null;  
    }
}
```

> 复杂度分析

寻找前缀，时间复杂度O(m)

额外使用node数组用，空间复杂度O(n)

> 总结

Runtime: 32 ms, faster than 65.99% of Java online submissions for Implement Trie (Prefix Tree).

Memory Usage: 48.5 MB, less than 89.03% of Java online submissions for Implement Trie (Prefix Tree).
