### LeetCode-79-Word-Search

> 题目链接

[LeetCode-79-Word-Search](https://leetcode.com/problems/word-search/)

> 思路

回溯法逐个比较字串，最外层需要查找起点。

> 代码

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        boolean[][] position = new boolean[board.length][board[0].length];
        for(int i = 0; i < board.length; i++)
            for(int j = 0; j < board[0].length; j++)
                if(findString(board, position, word, 0, i, j)) return true;
        return false;
    }
    public boolean findString(char[][] board, boolean[][] area, String word, int i, int x, int y){
        if(y < 0 || y == board[0].length) return false;
        if(x < 0 || x == board.length) return false;
        if(area[x][y] || board[x][y] != word.charAt(i)) return false;
        area[x][y] = true;
        if(i == word.length() - 1) return true;
        boolean exist = findString(board, area, word, i + 1, x + 1, y)||
            findString(board, area, word, i + 1, x, y + 1)||
            findString(board, area, word, i + 1, x - 1, y)||
            findString(board, area, word, i + 1, x, y - 1);
        area[x][y] = false;
        return exist;
    }
}
```

> 复杂度分析

全坏情况除第一个字母外，全部是同一个字母，且字串的长度是n * m，时间复杂度O((n * m)!)

额外使用二维boolean数组，空间复杂度O(n * m)

> 总结

Runtime: 6 ms, faster than 66.12% of Java online submissions for Word Search.

Memory Usage: 47.4 MB, less than 5.01% of Java online submissions for Word Search.
