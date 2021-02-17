### LeetCode-419-Battleships-in-a-Board

> 题目链接

[LeetCode-419-Battleships-in-a-Board](https://leetcode.com/problems/battleships-in-a-board/)

> 思路

计算战舰的数量，不能有相邻，必须有.隔开

> 代码

```java
class Solution {
    public int countBattleships(char[][] board) {
        int count = 0;
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                if (board[i][j] == 'X' && (i == 0 || board[i - 1][j] == '.') && (j == 0 || board[i][j - 1] == '.')) {
                    count++;
                }
            }
        }
        return count;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

额外使用count，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Battleships in a Board.

Memory Usage: 38.4 MB, less than 90.26% of Java online submissions for Battleships in a Board.
