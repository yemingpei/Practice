### LeetCode-face-17-15

> 题目链接

[LeetCode-face-17-15](https://leetcode-cn.com/problems/longest-word-lcci/)

> 思路

先排序，然后再判断这个词可以由其他值组合，深度遍历寻找

> 代码

```java
class Solution {
    public String longestWord(String[] words) {
        Arrays.sort(words, (a, b) -> {
            if(a.length() != b.length()) return b.length() - a.length();
            else return a.compareTo(b);
        });
        for(int i = 0; i < words.length; i++){
            if(isVaild(i, 0, words, words[i])) return words[i];
        }
        return "";
    }
    public boolean isVaild(int index, int k, String[] words, String word){
        for(int i = index + 1; i < words.length; i++){
            if((k + words[i].length()) > word.length() || word.indexOf(words[i], k) != k) continue;
            if((k + words[i].length()) == word.length())return true;
            if(isVaild(index, k + words[i].length(), words, word)) return true;
        }
        return false;
    }
}
```

> 复杂度分析

先排序，然后遍历，遍历里面还有递归，时间复杂度O(n!)

额外使用递归栈，递归深度，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了96.78%的用户

内存消耗：36.4 MB, 在所有 Java 提交中击败了96.46%的用户
