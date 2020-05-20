### LeetCode-36-Valid-Sudoku

> 题目链接

[LeetCode-36-Valid-Sudoku](https://leetcode.com/problems/valid-sudoku/)

> 思路

遍历9x9的九宫格，记录，行和列，以及小九宫是否存在此数据，如果有，就返回false，没有最后输出true

> 代码

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        int[][] row = new int[9][9];
        int[][] column = new int[9][9];
        int[][] bucket = new int[9][9];
        for (int i = 0; i < 9; i++)
          for (int j = 0; j < 9; j++) {
            if (board[i][j] != '.') {
              int number = board[i][j] - '1';
              if (row[i][number] == 1) return false;
              else row[i][number] = 1;

              if (column[j][number] == 1) return false;
              else column[j][number] = 1;

              int serial = i / 3 * 3 + j / 3;
              if (bucket[serial][number] == 1) return false;
              else bucket[serial][number] = 1;
            }
          }
        return true;
    }
}
```

> 复杂度分析

数独9x9固定长度，时间复杂度O(1)

额外使用了3个9x9的空间，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Valid Sudoku.

Memory Usage: 39.2 MB, less than 100.00% of Java online submissions for Valid Sudoku.
