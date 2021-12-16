### LeetCode-566-reshape-the-matrix

> 题目链接

[LeetCode-566-reshape-the-matrix](https://leetcode-cn.com/problems/reshape-the-matrix/)

> 思路

转化二维数组的长度关系result[sum / c][sum % c] = mat[i][j]

> 代码

```java
class Solution {
    public int[][] matrixReshape(int[][] mat, int r, int c) {
        if(r * c != mat.length * mat[0].length) return mat;
        int[][] result = new int[r][c];
        for(int i = 0; i < mat.length; i++)
            for(int j = 0; j < mat[0].length; j++){
                int sum = i * mat[0].length + j;
                result[sum / c][sum % c] = mat[i][j];
            }
        return result;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(nm)

额外使用常量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了31.96%的用户

内存消耗：39.3 MB, 在所有 Java 提交中击败了45.91%的用户
