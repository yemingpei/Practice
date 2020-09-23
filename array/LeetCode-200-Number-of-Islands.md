### LeetCode-200-Number-of-Islands

> 题目链接

[LeetCode-200-Number-of-Islands](https://leetcode.com/problems/number-of-islands/)

> 思路

遇到1就开始递归遍历四个方向，把全部1变成0，此为一个岛屿，剩下的操作也一样。

> 代码

```java
class Solution {
    public int numIslands(char[][] grid) {
        int result = 0;
        int row = grid.length;
        if(row != 0){
            int column = grid[0].length;
            for(int i = 0; i < row; i++)
                for(int j = 0; j <column; j++){
                    if(grid[i][j] == '1'){
                        result++;
                        findIsland(grid, i, j, row - 1,  column - 1);
                    }
                }
        }
        return result;
    }
    public void findIsland(char[][] grid, int i, int j, int rowPosition, int columnPosition){
        grid[i][j] = '0';
        if(i != 0 && grid[i - 1][j] == '1') findIsland(grid, i - 1, j, rowPosition, columnPosition);
        if(j != 0 && grid[i][j - 1] == '1') findIsland(grid, i, j - 1, rowPosition, columnPosition);
        if(j < columnPosition && grid[i][j + 1] == '1') findIsland(grid, i, j + 1, rowPosition, columnPosition);
        if(i < rowPosition && grid[i + 1][j] == '1') findIsland(grid, i + 1, j, rowPosition, columnPosition);
    }
}
```

> 复杂度分析

最多每个点遍历两遍，时间复杂度O(n ^ 2)

无额外使用辅助变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.95% of Java online submissions for Number of Islands.

Memory Usage: 42.1 MB, less than 53.93% of Java online submissions for Number of Islands.
