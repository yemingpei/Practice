### LeetCode-face-01-07

> 题目链接

[LeetCode-face-01-07](https://leetcode-cn.com/problems/rotate-matrix-lcci/)

> 思路

利用旋转的规律，[i][j] -> [n - j - 1][i], [n - j - 1][i] -> [n - i - 1][n - j - 1], [n - i - 1][n - j - 1] -> [j][n - i - 1], [j][n - i - 1]  -> [i][j]

> 代码

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for (int i = 0; i < n / 2; ++i) {
            for (int j = 0; j < (n + 1) / 2; ++j) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[n - j - 1][i];
                matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1];
                matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1];
                matrix[j][n - i - 1] = temp;
            }
        }
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(mn)

额外使用一个常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.7 MB, 在所有 Java 提交中击败了10.76%的用户
