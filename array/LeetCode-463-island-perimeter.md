### LeetCode-463-island-perimeter

> 题目链接

[LeetCode-463-island-perimeter](https://leetcode-cn.com/problems/island-perimeter/)

> 思路

利用深度优先检索，寻找第一个大陆，递归输出边的总和

> 代码

```java
class Solution {
    public int islandPerimeter(int[][] grid) {
        int row = grid.length - 1;
        int coulmn = grid[0].length - 1;
        for(int i = 0; i <= row; i++)
            for(int j = 0; j <= coulmn; j++){
                if(grid[i][j] == 1) return countLand(grid, i, j, row, coulmn);
            }
        return 0;
    }
    public int countLand(int[][] grid, int i, int j, int xMax, int yMax){
        grid[i][j] = -1;
        int count = 0;
        if(i > 0){
            int number = grid[i - 1][j];
            if(number == 0) count++;
            if(number == 1) count += countLand(grid, i - 1, j, xMax, yMax);
        }
        else count++;
        if(j > 0){
            int number = grid[i][j - 1];
            if(number == 0) count++;
            if(number == 1) count += countLand(grid, i, j - 1, xMax, yMax);
        }
        else count++;
        if(i < xMax){
            int number = grid[i + 1][j];
            if(number == 0) count++;
            if(number == 1) count += countLand(grid, i + 1, j, xMax, yMax);
        }
        else count++;
        if(j < yMax){
            int number = grid[i][j + 1];
            if(number == 0) count++;
            if(number == 1) count += countLand(grid, i, j + 1, xMax, yMax);
        }
        else count++;
        return count;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

额外使用int辅助计算，空间复杂度O(1)

> 总结

执行用时：9 ms, 在所有 Java 提交中击败了65.15%的用户

内存消耗：40 MB, 在所有 Java 提交中击败了41.26%的用户
