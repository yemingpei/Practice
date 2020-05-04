### LeetCode-74-Search-a-2D-Matrix

> 题目链接

[LeetCode-74-Search-a-2D-Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

> 思路

二分查找，只要问题在于还原mid在矩阵中的位置，mid / column为行，mid % column为列

> 代码

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int low = matrix.length;
        if(low == 0) return false;
        int column = matrix[0].length;
            if(column == 0) return false;
        int left = 0;
        int right = low * column - 1;
        while (right >= left) {
          int mid = left + ((right - left) >> 1);
          int i = mid / column;
          int j = mid % column;
          if (matrix[i][j] == target) return true;
          else if (matrix[i][j] > target) right = mid - 1;
          else left = mid + 1;
        }
        return false;
    }
}
```

> 复杂度分析

二分查找，还原mid在二维矩阵的位置，时间复杂度O(lgn)

额外使用了左右边界和中间的位置的指标，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Search a 2D Matrix.

Memory Usage: 39 MB, less than 25.76% of Java online submissions for Search a 2D Matrix.
