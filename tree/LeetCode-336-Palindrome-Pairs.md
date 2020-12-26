### LeetCode-336-Palindrome-Pairs

> 题目链接

[LeetCode-336-Palindrome-Pairs](https://leetcode.com/problems/palindrome-pairs/)

> 思路

字典树查询，暴力查询回文串，可以利用 manacher减少比较的次数

> 代码

```java
class Solution {
    private static class TrieNode {
        TrieNode[] children;
        int index;
        List<Integer> list;
        TrieNode() {
            children = new TrieNode[26];
            index = -1;
            list = new ArrayList<>();
        }
    }
    
    public List<List<Integer>> palindromePairs(String[] words) {
        TrieNode root = new TrieNode();
        for (int i = 0; i < words.length; i++) {
            addWord(root, words[i], i);
        }
        List<List<Integer>> res = new ArrayList<>();
        for (int i = 0; i < words.length; i++) {
            search(words, i, root, res);
        }
        
        return res;
    }
    
    private void addWord(TrieNode root, String word, int index) {
        int len = word.length();
        for (int i = len-1; i >= 0; i--) {
            char c = word.charAt(i);
            int j = c-'a';
            if (root.children[j] == null) {
                root.children[j] = new TrieNode();
            }
            
            if (isPalindrome(word, 0, i)) {
                root.list.add(index);
            }
            root = root.children[j];
        }
        root.list.add(index);
        root.index = index;
    }
    
    private void search(String[] words, int currIndex, TrieNode root, List<List<Integer>> res) {
        int len = words[currIndex].length();
        for (int i = 0; i < len; i++) {
            if (root.index >= 0 
                && root.index != currIndex 
                && isPalindrome(words[currIndex], i, len-1)) {
                res.add(Arrays.asList(currIndex, root.index));
            }
            root = root.children[words[currIndex].charAt(i)-'a'];
            if (root == null) return;
        }
        for (int index : root.list) {
            if (index == currIndex) continue;
            res.add(Arrays.asList(currIndex,index));
        }
    }
    
    private boolean isPalindrome(String word, int start, int end) {
        while (start < end) {
            if (word.charAt(start++) != word.charAt(end--)) return false;
        }
        return true;
    }
}
```

> 复杂度分析

暴力比较法，时间复杂度O(n × m)

使用字典树保存必要的信息，空间复杂度O(n × m)

> 总结

Runtime: 63 ms, faster than 56.16% of Java online submissions for Palindrome Pairs.

Memory Usage: 116 MB, less than 5.09% of Java online submissions for Palindrome Pairs.
