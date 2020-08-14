### LeetCode-130-Surrounded-Regions

> 题目链接

[LeetCode-130-Surrounded-Regions](https://leetcode.com/problems/surrounded-regions/)

> 思路

作为入口，把可达的O先标记为A，最后再还原回来

> 代码

```java
class Solution {
    public void solve(char[][] board) {
        int row = board.length;
        if(row < 3) return;
        int column = board[0].length;
        if(column < 3) return;
        for(int i = 0; i < row; i++){
            if(board[i][0] == 'O') markPoint(board, i, 0, row -1, column - 1);
            if(board[i][column - 1] == 'O') markPoint(board, i, column - 1, row -1, column - 1);
        }
        for(int i = 0; i < column; i++){
            if(board[0][i] == 'O') markPoint(board, 0, i, row -1, column - 1);
            if(board[row -1][i] == 'O') markPoint(board, row -1, i, row -1, column - 1);
        }
        for(int i = 0; i < row; i++)
            for(int j = 0; j < column; j++){
                if(board[i][j] == 'A') board[i][j] = 'O';
                else board[i][j] = 'X';
            }
    }
    public void markPoint(char[][] board, int row, int column, int rowBorder, int columnBorder){
        board[row][column] = 'A';
        if(row > 0 && board[row - 1][column] == 'O') markPoint(board, row - 1, column, rowBorder, columnBorder);
        if(column > 0 && board[row][column - 1] == 'O') markPoint(board, row, column - 1, rowBorder, columnBorder);
        if(row < rowBorder && board[row + 1][column] == 'O') markPoint(board, row + 1, column, rowBorder, columnBorder);
        if(column < columnBorder && board[row][column + 1] == 'O') markPoint(board, row, column + 1, rowBorder, columnBorder);
    }
}
```

> 复杂度分析

需要全部点，时间复杂度O(n ^ 2)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.33% of Java online submissions for Surrounded Regions.

Memory Usage: 41.9 MB, less than 32.08% of Java online submissions for Surrounded Regions.
