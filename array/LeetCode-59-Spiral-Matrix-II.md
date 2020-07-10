### LeetCode-59-Spiral-Matrix-II

> 题目链接

[LeetCode-59-Spiral-Matrix-II](https://leetcode.com/problems/spiral-matrix-ii/)

> 思路

每一圈为一个单位，依次从小到大填数字，模拟填数字的过程，实现即可

> 代码

```java
class Solution {
    public int[][] generateMatrix(int n) {
        int top = 0;
        int left = 0;
        int right = n - 1;
        int bottom = n - 1;
        int count = 1;
        int[][] result = new int[n][n];
        while(left <= right){
            for(int i = left; i <= right; i++){
                result[top][i] = count;
                count++;
            }
            top++;
            for(int i = top; i <= bottom; i++){
                result[i][right] = count;
                count++;
            }
            right--;
            for(int i = right; i >= left; i--){
                result[bottom][i] = count;
                count++;
            }
            bottom--;
            for(int i = bottom; i >= top; i--){
                result[i][left] = count;
                count++;
            }
            left++;
        }
        return result;
    }
}
```

> 复杂度分析

需要填完大小n * n的二维数组数组，时间复杂度O(n * n)

额外使用五个int值来辅助，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Spiral Matrix II.

Memory Usage: 39.4 MB, less than 5.28% of Java online submissions for Spiral Matrix II.
