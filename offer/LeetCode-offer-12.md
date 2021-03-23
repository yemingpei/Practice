### LeetCode-offer-12

> 题目链接

[LeetCode-offer-12](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/)

> 思路

回溯法，不断检测字符是否匹配，二维布尔数组用来记录走过的路径，走完就要释放，检索到结果就提前返回

> 代码

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        int row = board.length;
        int column = board[0].length;
        boolean[][] area = new boolean[row][column];
        for(int i = 0; i < row; i ++)
            for(int j = 0; j < column; j++){
                if(board[i][j] == word.charAt(0) && search(board, word, area, 1, i, j, row -1, column - 1)) return true;
            }
        return false;
    }
    public boolean search(char[][] board, String word, boolean[][] area, int position, int i, int j, int row, int column){
        if(position == word.length()) return true;
        area[i][j] = true;
        if((i > 0 && !area[i - 1][j] && board[i - 1][j] == word.charAt(position)))
            if(search(board, word, area, position + 1, i - 1, j, row, column)) return true;
        if(j > 0 && !area[i][j - 1] && board[i][j - 1] == word.charAt(position))
            if(search(board, word, area, position + 1, i, j - 1, row, column)) return true;
        if(j < column && !area[i][j + 1] && board[i][j + 1] == word.charAt(position))
            if(search(board, word, area, position + 1, i, j + 1, row, column)) return true;
        if(i < row && !area[i + 1][j] && board[i + 1][j] == word.charAt(position))
            if(search(board, word, area, position + 1, i + 1, j, row, column)) return true;
        area[i][j] = false;
        return false;
    }
}
```

> 复杂度分析

DFS + 剪枝，时间复杂度O(n ^ 2)

额外使用二维布尔数组，空间复杂度O(n ^ 2)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了98.27%的用户

内存消耗：40.2 MB, 在所有 Java 提交中击败了66.80%的用户

