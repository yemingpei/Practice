### LeetCode-37-Sudoku-Solver

> 题目链接

[LeetCode-37-Sudoku-Solver](https://leetcode.com/problems/sudoku-solver/)

> 思路

暴力法，不断寻找所在行，列，小九宫没有出现的数字，不断递归推导，完成数独填写

> 代码

```java
class Solution {
    boolean[][] rows = new boolean[10][10];
    boolean[][] cols = new boolean[10][10];
    boolean[][] sqrs = new boolean[10][10];
    public void solveSudoku(char[][] board) {
        List<int[]> blank = new ArrayList<>();
        for (int i = 0; i < board.length; ++i){
            for (int j = 0; j < board[0].length; ++j){
                if (board[i][j] == '.') blank.add(new int[] {i, j});
                else {
                    int num = board[i][j] - '0';
                    rows[i][num] = cols[j][num] = sqrs[i / 3 * 3 + j / 3][num] = true;
                }
            }
        }
        fill(board, blank, 0);
    }
    
    private boolean fill(char[][] board, List<int[]> blanks, int index) {
        if (index == blanks.size()) return true;
        int i = blanks.get(index)[0];
        int j = blanks.get(index)[1];
        for (int num = 1; num <= 9; ++num){
            if (!rows[i][num] && !cols[j][num] && !sqrs[i / 3 * 3 + j / 3][num]){
                rows[i][num] = cols[j][num] = sqrs[i / 3 * 3 + j / 3][num] = true;
                board[i][j] = (char)(num + '0');
                if (fill(board, blanks, index + 1)) return true;
                rows[i][num] = cols[j][num] = sqrs[i / 3 * 3 + j / 3][num] = false;
                board[i][j] = '.';
            }
        }
        return false;
    }
}
```

> 复杂度分析

因为是九宫格，数据长为81，时间复杂度O(1)

因为是九宫格，数据长为81，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 99.25% of Java online submissions for Sudoku Solver.

Memory Usage: 36.7 MB, less than 22.81% of Java online submissions for Sudoku Solver.
