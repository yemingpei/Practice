### LeetCode-85-Maximal-Rectangle

> 题目链接

[LeetCode-85-Maximal-Rectangle](https://leetcode.com/problems/maximal-rectangle/)

> 思路

将输入拆分成一系列的柱状图，每个柱状图代表一列的子结构。为了计算长方形的最大面积，我们仅仅需要计算每个柱状图中的最大面积并找到全局最大值

> 代码

```java
class Solution {
    public int maximalRectangle(char[][] matrix) {
        if (matrix == null || matrix.length == 0) return 0;
        int row = matrix.length, col = matrix[0].length;
        int[] heights = new int[col];
        int res = 0;
        for (int i = 0; i < row; i++) {
            updateHeights(heights, matrix, i);
            res = Math.max(res, updateArea(heights));
        }
        return res;
    }
    private void updateHeights(int[] heights, char[][] matrix, int row) {
        for (int j = 0; j < matrix[0].length; j++) {
            if (matrix[row][j] == '0') heights[j] = 0;
            else heights[j] ++;
        }
    }
    private int updateArea(int[] heights) {
        int res = -1;
        int[] stack = new int[heights.length]; 
        int index = -1;
        for (int i = 0; i <= heights.length; i++) {
            int h = (i == heights.length? -1: heights[i]);
            while (index != -1 && h < heights[stack[index]]) {
                int curH = heights[stack[index--]];
                res = Math.max(res, curH * (index == -1?i: i - stack[index] - 1));
            }
            stack[++index] = i;
        }
        return res;
    }
}
```

> 复杂度分析

遍历整个二维数组，时间复杂度为O(n * m)

额外使用了数组来记录柱状图的信息，空间复杂度O(m)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Maximal Rectangle.

Memory Usage: 42.2 MB, less than 87.64% of Java online submissions for Maximal Rectangle.
