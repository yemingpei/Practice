### LeetCode-240-Search-a-2D-Matrix-II

> 题目链接

[LeetCode-240-Search-a-2D-Matrix-II](https://leetcode.com/problems/search-a-2d-matrix-ii/)

> 思路

从左下角开始寻找，如果target比当前位置大，则需要减少，则往上移动；如果target比当前位置小，则需要增大，则往右移动，所以只能往上和右移动。

> 代码

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = matrix.length - 1;
        int column = 0;
        while(row >= 0 && column < matrix[0].length){
            if(matrix[row][column] > target)
                row--;
            else if(matrix[row][column] < target)
                column++;
            else return true;
        }
        return false;
    }
}
```

> 复杂度分析

横向次数不超过列的数量，纵向次数不超过行的数量，时间复杂度O(m + n)

需要两个常量int来记录移动的位置，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 100.00% of Java online submissions for Search a 2D Matrix II.

Memory Usage: 44.5 MB, less than 11.51% of Java online submissions for Search a 2D Matrix II.
