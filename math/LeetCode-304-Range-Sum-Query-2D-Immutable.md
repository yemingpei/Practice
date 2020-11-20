### LeetCode-304-Range-Sum-Query-2D-Immutable

> 题目链接

[LeetCode-304-Range-Sum-Query-2D-Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)

> 思路

region保存左上角到i，j的面积，面积的公式为region[i][j] = region[i][j - 1] + region[i - 1][j] + matrix[i][j] - region[i - 1][j - 1]。

sumRegion的公式为region[row2][col2] + region[row1 - 1][col1 - 1] - region[row1 - 1][col2] - region[row2][col1 - 1]

> 代码

```java
class NumMatrix {
    private int[][] region;
    public NumMatrix(int[][] matrix) {
        if(matrix.length == 0 || matrix[0].length == 0) return;
        region = new int[matrix.length][matrix[0].length];
        region[0][0] = matrix[0][0];
        for(int i = 1; i < matrix.length; i++)
            region[i][0] = region[i - 1][0] + matrix[i][0];
        for(int j = 1; j < matrix[0].length; j++)
            region[0][j] = region[0][j - 1] + matrix[0][j];
        for(int i = 1; i < matrix.length; i++)
            for(int j = 1; j < matrix[0].length; j++){
                 region[i][j] = region[i][j - 1] + region[i - 1][j] + matrix[i][j] - region[i - 1][j - 1];
            }
    }
    
    public int sumRegion(int row1, int col1, int row2, int col2) {
        if(row1 != 0 && col1 != 0)
            return region[row2][col2] + region[row1 - 1][col1 - 1] - region[row1 - 1][col2] - region[row2][col1 - 1];
        else if(row1 == 0 && col1 == 0)
            return region[row2][col2];
        else if(row1 == 0)
            return region[row2][col2] - region[row2][col1 - 1];
        else return region[row2][col2] - region[row1 - 1][col2];
    }
}
```

> 复杂度分析

NumMatrix构造函数，时间复杂度O(mn)，sumRegion的时间复杂度是O(1)

需要二维数组来保存结果，空间复杂度O(mn)

> 总结

Runtime: 10 ms, faster than 100.00% of Java online submissions for Range Sum Query 2D - Immutable.

Memory Usage: 44.7 MB, less than 54.81% of Java online submissions for Range Sum Query 2D - Immutable.
