### LeetCode-offer-47

> 题目链接

[LeetCode-offer-47](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

> 思路

只能向下或者向右，所以有result[j] = Math.max(result[j], result[j - 1]) + grid[i][j]，动态规划公式

> 代码

```java
class Solution {
    public int maxValue(int[][] grid) {
        int row = grid.length;
        int column = grid[0].length;
        int[] result = new int[column];
        for(int i = 0; i < column; i++){
            if(i == 0) result[i] = grid[0][i];
            else result[i] = result[i - 1] + grid[0][i];
        }
        for(int i = 1; i < row; i++)
            for(int j = 0; j < column; j++){
                if(j == 0) result[j] = result[j] + grid[i][j];
                else result[j] = Math.max(result[j], result[j - 1]) + grid[i][j];
            }
        return result[column - 1];
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(nm)

额外使用辅助记录数据，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了98.43%的用户

内存消耗：41.2 MB, 在所有 Java 提交中击败了53.72%的用户
