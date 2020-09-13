### LeetCode-212-Word-Search-II

> 题目链接

[LeetCode-212-Word-Search-II](https://leetcode.com/problems/word-search-ii/)

> 思路

利用字典树查询字符串，避免查找失败时候的重复操作

> 代码

```java
class Solution {
    public List<String> findWords(char[][] board, String[] words) {
        final TrieNode root = new TrieNode();
        for (String word : words) {
            root.add(word, 0);
        }
        
        final List<String> out = new ArrayList<>();
        final int R = board.length;
        final int C = board[0].length;
        for (int r = 0; r < R; r++) {
            for (int c = 0; c < C; c++) {
                find(board, r, c, root, out);
                if (root.size == 0) return out;
            }
        }
        
        return out;
    }
    
    private static int find(char[][] board, int r, int c, TrieNode node, List<String> out) {
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length) return 0;
        char ch = board[r][c];
        if (ch == '#') return 0;
        TrieNode next = node.next(ch);
        if (next == null) return 0;
        board[r][c] = '#';
        int less = 0;
        less += find(board, r+1, c, next, out);
        less += find(board, r-1, c, next, out);
        less += find(board, r, c+1, next, out);
        less += find(board, r, c-1, next, out);
        String word = next.word;
        if (word != null) {
            out.add(word);
            next.word = null;
            less += 1;
        }
        if ((next.size -= less) == 0) {
            node.remove(ch);   
        }
        board[r][c] = ch;
        return less;
    }
    
    private static class TrieNode {
        private TrieNode children[];
        private String word;
        private int size;
        
        private void add(String w, int i) {
            if (w.length() == i) {
                word = w;
            } else {
                if (children == null) {
                    children = new TrieNode[26];
                }
                int cIdx = w.charAt(i) - 'a';
                TrieNode child = children[cIdx];
                if (child == null) {
                    child = new TrieNode();
                    children[cIdx] = child;
                }
                child.add(w, i+1);
            }
            size += 1;
        }
        
        private TrieNode next(char c) {
            return children == null ? null : children[c - 'a'];
        }
        
        private TrieNode remove(char c) {
            return children[c - 'a'] = null;
        }
    }
}
```

> 复杂度分析

通过字典树比较矩阵中的字符，时间复杂度O(n ^ 2 * m * logm)

使用字典树，空间复杂度O(m)

> 总结

Runtime: 7 ms, faster than 99.91% of Java online submissions for Word Search II.

Memory Usage: 45.1 MB, less than 76.68% of Java online submissions for Word Search II.
