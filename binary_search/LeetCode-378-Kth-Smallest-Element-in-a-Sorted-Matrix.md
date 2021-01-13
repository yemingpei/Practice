### LeetCode-378-Kth-Smallest-Element-in-a-Sorted-Matrix

> 题目链接

[LeetCode-378-Kth-Smallest-Element-in-a-Sorted-Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

> 思路

利用中间值的特点，不断缩小峰值的范围，注意二分的循环判断，非左即右，利用题目给得相邻的数字不相等。

> 代码

```java
class Solution {
    public int kthSmallest(int[][] matrix, int k) {
        int n = matrix.length;
        int left = matrix[0][0];
        int right = matrix[n - 1][n - 1];
        while (left < right) {
            int mid = left + ((right - left) >> 1);
            if (check(matrix, mid, k, n)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }

    public boolean check(int[][] matrix, int mid, int k, int n) {
        int i = n - 1;
        int j = 0;
        int num = 0;
        while (i >= 0 && j < n) {
            if (matrix[i][j] <= mid) {
                num += i + 1;
                j++;
            } else {
                i--;
            }
        }
        return num >= k;
    }
}
```

> 复杂度分析

不断利用中点缩小峰值的范围，时间复杂度O(nlgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Kth Smallest Element in a Sorted Matrix.

Memory Usage: 44.9 MB, less than 29.00% of Java online submissions for Kth Smallest Element in a Sorted Matrix.
