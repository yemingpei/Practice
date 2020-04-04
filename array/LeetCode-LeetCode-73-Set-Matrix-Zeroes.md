### LeetCode-73-Set-Matrix-Zeroes

> 题目链接

[LeetCode-73-Set-Matrix-Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

> 思路

用第一行和第一列来记录对应行列的0的位置，因为[0，0]，这个位置冲突，所以单独检查第一行，把[0,0]作为列的凭证，记录完位置就开始遍历列，更换对应的行，然后遍历行，更换对应的列，最后检查行是否需要更换

> 代码

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int vertical = matrix.length, horizontal = matrix[0].length;
        boolean horizontalFlag = false;
        for (int i = 0; i < horizontal; i++)
          if (matrix[0][i] == 0) {
            horizontalFlag = true;
            break;
          }
        for (int i = 1; i < vertical; i++)
          for (int j = 0; j < horizontal; j++)
            if (matrix[i][j] == 0) {
              matrix[0][j] = 0;
              matrix[i][0] = 0;
            }
        for (int i = 1; i < vertical; i++)
          if (matrix[i][0] == 0)
            for (int j = 0; j < horizontal; j++)
              matrix[i][j] = 0;
        for (int j = 0; j < horizontal; j++)
          if (matrix[0][j] == 0)
            for (int i = 0; i < vertical; i++)
              matrix[i][j] = 0;
        if (horizontalFlag)
          for (int j = 0; j < horizontal; j++)
            matrix[0][j] = 0;
     }
}
```

> 复杂度分析

首先for循环了一遍数组，用时m*n，然后竖向遍历第一列，更换对应的行，最坏情况也是m*n，再横向遍历第一行，更换对应的列，最坏情况也是m*n，最后检查第一行的换0情况，总用时是3*m*n，时间复杂度O(m*n)

额外使用了3个变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 89.35% of Java online submissions for Set Matrix Zeroes.
Memory Usage: 40.9 MB, less than 98.57% of Java online submissions for Set Matrix Zeroes.
