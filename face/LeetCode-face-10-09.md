### LeetCode-face-10-09

> 题目链接

[LeetCode-face-10-09](https://leetcode-cn.com/problems/sorted-matrix-search-lcci/)

> 思路

从左下角开始比较，如果大就向上移动，小就向右移动，超出边界就输出false

> 代码

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = matrix.length;
        if(row == 0) return false;
        int column = matrix[0].length;
        if(column == 0) return false;
        int m = 0;
        int n = row - 1;
        while(m < column && n >= 0){
            if(matrix[n][m] == target) return true;
            if(matrix[n][m] > target) n--;
            else m++;
        }
        return false;
    }
}
```

> 复杂度分析

底部开始检索，时间复杂度O(m + n) 

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：43.9 MB, 在所有 Java 提交中击败了48.34%的用户
