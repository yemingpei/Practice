### LeetCode-face-16-04

> 题目链接

[LeetCode-face-16-04](https://leetcode-cn.com/problems/tic-tac-toe-lcci/)

> 思路

遍历计算每个行和列的数量，斜边的数量，通过数量来判断是否能赢或者输

> 代码

```java
class Solution {
    public String tictactoe(String[] board) {
        int xieX = 0, xieO = 0, fanX = 0, fanO = 0;
        int length = board.length;
        int[] columnX = new int[length];
        int[] columnO = new int[length];
        boolean flag = false;
        for(int i = 0; i < length; i++){
            int rowX = 0, rowO = 0;
            for(int j = 0; j < length; j++){
                char c = board[i].charAt(j);
                if(c == 'O'){
                    rowO++;
                    columnO[j]++;
                    if(i == j) xieO++;
                    if(i + j == length - 1) fanO++;
                }
                else if(c == 'X'){
                    rowX++;
                    columnX[j]++;
                    if(i == j) xieX++;
                    if(i + j == length - 1) fanX++;
                }
                else flag = true;
            }
            if(rowX == length) return "X";
            if(rowO == length) return "O";
        }
        if(xieX == length || fanX == length) return "X";
        if(xieO == length || fanO == length) return "O";
        for(int i : columnX){
            if(i == length) return "X";
        }
        for(int i : columnO){
            if(i == length) return "O";
        }
        return flag ? "Pending" : "Draw";
    }
}
```

> 复杂度分析

双重遍历，时间复杂度O(n ^ 2)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了88.54%的用户

内存消耗：36.6 MB, 在所有 Java 提交中击败了32.29%的用户
