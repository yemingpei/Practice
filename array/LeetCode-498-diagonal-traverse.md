### LeetCode-498-diagonal-traverse

> 题目链接

[LeetCode-498-diagonal-traverse](https://leetcode-cn.com/problems/diagonal-traverse/)

> 思路

模拟对角线的数据选择，需要增加边界的判断

> 代码

```java
class Solution {
    public int[] findDiagonalOrder(int[][] mat) {
        if (mat == null || mat.length == 0) return new int[]{};
        int row = mat.length;
        int col = mat[0].length;
        int[] res = new int[row * col];
        int index = 0;
        int m = 0;
        int n = 0;
        for (int i = 0; i < row + col - 1; i++) {
            if (i % 2 == 0) {
                while (m >= 0 && n <= col - 1) {
                    res[index++] = mat[m][n];
                    m--;
                    n++;
                }
                if (n < col) m++;
                else {
                    m += 2;
                    n--;
                }
            } else {
                while (m <= row - 1 && n >= 0) {
                    res[index++] = mat[m][n];
                    m++;
                    n--;
                }
                if (m < row) n++;
                else {
                    n += 2;
                    m--;
                }
            }
        }
        return res;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(m * n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：40.6 MB, 在所有 Java 提交中击败了35.70%的用户
