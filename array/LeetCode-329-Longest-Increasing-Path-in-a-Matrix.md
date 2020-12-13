### LeetCode-329-Longest-Increasing-Path-in-a-Matrix

> 题目链接

[LeetCode-329-Longest-Increasing-Path-in-a-Matrix](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/)

> 思路

用数组保存最大值，用深度遍历的方式找出最长的递增连，顺便记录对应位置最长的数量，就可以避免重复计算，判断

> 代码

```java
class Solution {
    public int longestIncreasingPath(int[][] matrix) {
        int row = matrix.length;
        if(row == 0) return 0; 
        int column = matrix[0].length;
        if(column == 0) return 0;
        int[] number = new int[row * column];
        int max = 0;
        for(int i = 0; i < row; i++){
            for(int j = 0; j < column; j++){
                max = Math.max(max, findMaxNumber(i, j, number, row, column, matrix));
            }
        }
        return max;
    }
    public int findMaxNumber(int i, int j, int[] number,int row, int column, int[][] matrix){
        int n = i * column + j;
        if(number[n] != 0) return number[n];
        int max = 1;
        if(i > 0 && matrix[i - 1][j] > matrix[i][j]) max = Math.max(max,findMaxNumber(i - 1, j, number, row, column, matrix) + 1);
        if(j > 0 && matrix[i][j - 1] > matrix[i][j]) max = Math.max(max,findMaxNumber(i, j - 1, number, row, column, matrix) + 1);
        if(i < row -1 && matrix[i + 1][j] > matrix[i][j]) max = Math.max(max,findMaxNumber(i + 1, j, number, row, column, matrix) + 1);
        if(j < column - 1 && matrix[i][j + 1] > matrix[i][j]) max = Math.max(max,findMaxNumber(i, j + 1, number, row, column, matrix) + 1);
        number[n] = max;
        return max;
    } 
}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

需要数组来记录每个位置的最大值，避免重复计算，空间复杂度O(mn)

> 总结

Runtime: 5 ms, faster than 100.00% of Java online submissions for Longest Increasing Path in a Matrix.

Memory Usage: 39.6 MB, less than 28.52% of Java online submissions for Longest Increasing Path in a Matrix.
