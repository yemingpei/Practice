### LeetCode-542-01-matrix

> 题目链接

[LeetCode-542-01-matrix](https://leetcode-cn.com/problems/01-matrix/)

> 思路

使用动态规划，先遍历一遍数据，修改1的数组为最大值，然后第二遍是从左到右，从上到下，值通过左边和上面的值以及当前的值推算，第三遍是从下到上，从右到左，值通过右边和下方的值以及当前的值来推算

> 代码

```java
class Solution {
    public int[][] updateMatrix(int[][] mat) {
        int x = mat.length;
        int y = mat[0].length;
        for (int i = 0; i < x; i++)
            for (int j = 0; j < y; j++) {
                if (mat[i][j] == 1) mat[i][j] = Integer.MAX_VALUE - 1;
            }
        for (int i = 0; i < x; i++)
            for (int j = 0; j < y; j++) {
                if (i > 0) mat[i][j] = Math.min(mat[i][j], mat[i - 1][j] + 1);
                if (j > 0) mat[i][j] = Math.min(mat[i][j], mat[i][j - 1] + 1);
            }
        for (int i = x - 1; i >= 0; i--)
            for (int j = y - 1; j >= 0; j--) {
                if (i < x - 1) mat[i][j] = Math.min(mat[i][j], mat[i + 1][j] + 1);
                if (j < y - 1) mat[i][j] = Math.min(mat[i][j], mat[i][j + 1] + 1);
            }
        return mat;
    }
}
```

> 复杂度分析

遍历三轮二维数组，时间复杂度O(nm)

额外使用常量的数据，空间复杂度O(1)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：41.4 MB, 在所有 Java 提交中击败了70.47%的用户
