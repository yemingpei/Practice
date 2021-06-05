### LeetCode-face-01-08

> 题目链接

[LeetCode-face-01-08](https://leetcode-cn.com/problems/zero-matrix-lcci/)

> 思路

用两个布尔值记录第一行和第一列，是否为0，然后就利用第一行和第一列作为里面内容的标记

> 代码

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        boolean flagCol0 = false, flagRow0 = false;
        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) {
                flagCol0 = true;
            }
        }
        for (int j = 0; j < n; j++) {
            if (matrix[0][j] == 0) {
                flagRow0 = true;
            }
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = matrix[0][j] = 0;
                }
            }
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }
        if (flagCol0) {
            for (int i = 0; i < m; i++) {
                matrix[i][0] = 0;
            }
        }
        if (flagRow0) {
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }
    }
}
```

> 复杂度分析

遍历两遍二维数组，时间复杂度O(mn)

额外使用两个常量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了41.67%的用户

内存消耗：39.3 MB, 在所有 Java 提交中击败了99.49%的用户
