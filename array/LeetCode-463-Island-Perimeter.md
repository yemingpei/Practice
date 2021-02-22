### LeetCode-463-Island-Perimeter

> 题目链接

[LeetCode-463-Island-Perimeter](https://leetcode.com/problems/island-perimeter/)

> 思路

遍历二维数组，然后计算是不是相邻的边，不是1相连就计算边数

> 代码

```java
class Solution {
    public int islandPerimeter(int[][] grid) {
        int cloumn = grid.length;
        int row = grid[0].length;
        int h = row - 1;
        int v = cloumn - 1;
        int result = 0;
        for(int i = 0; i < cloumn; i++)
            for(int j = 0; j < row; j++){
                if(grid[i][j] == 1){
                    if(i == 0 || grid[i - 1][j] == 0)    result++;
                    if(j == 0 || grid[i][j - 1] == 0)    result++;
                    if(i == v || grid[i + 1][j] == 0)    result++;
                    if(j == h || grid[i][j + 1] == 0)    result++;
                }
            }
        return result;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(mn)

额外使用常数个int，空间复杂度O(1)

> 总结

Runtime: 5 ms, faster than 99.60% of Java online submissions for Island Perimeter.

Memory Usage: 39.9 MB, less than 83.53% of Java online submissions for Island Perimeter.
