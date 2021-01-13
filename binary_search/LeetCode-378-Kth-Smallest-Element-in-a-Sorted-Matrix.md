### LeetCode-378-Kth-Smallest-Element-in-a-Sorted-Matrix

> 题目链接

[LeetCode-378-Kth-Smallest-Element-in-a-Sorted-Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

> 思路

利用中间值的特点，不断缩小峰值的范围，注意二分的循环判断，非左即右，利用题目给得相邻的数字不相等。

> 代码

```java
class Solution {
    public int kthSmallest(int[][] matrix, int k) {
        if (matrix == null || matrix.length == 0 || matrix[0] == null || matrix.length == 0) return -1;
        int m = matrix.length;
        int lo = matrix[0][0], hi = matrix[m - 1][m - 1];
        while (lo <= hi) {
            int mid = (hi - lo) / 2 + lo;
            int count = getLessEqual(matrix, mid);
            if (count < k) lo = mid + 1;
            else hi = mid - 1;
        }
        return lo;
    }

    private int getLessEqual(int[][] matrix, int num) {
        int m = matrix.length;
        int i = m - 1;
        int j = 0;    
        int count = 0;
        while (i >= 0 ) {
            while ( j < m && matrix[i][j] <= num) {
                j ++;
            }
            count += j;
            i--;
        }
        return count;
    }
}
```

> 复杂度分析

不断利用中点缩小峰值的范围，时间复杂度O(nlgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Kth Smallest Element in a Sorted Matrix.

Memory Usage: 44.9 MB, less than 29.00% of Java online submissions for Kth Smallest Element in a Sorted Matrix.
