### LeetCode-48-Rotate-Image

> 题目链接

[LeetCode-48-Rotate-Image](https://leetcode.com/problems/rotate-image/)

> 思路

模拟旋转，找出每四个位置交换的规律

> 代码

```java
class Solution {
    public void rotate(int[][] matrix) {
        int l=matrix.length;
        for(int i=0;i<l/2;i++){
            for(int j=i;j<l-i-1;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[l-j-1][i];
                matrix[l-j-1][i]=matrix[l-i-1][l-j-1];
                matrix[l-i-1][l-j-1]=matrix[j][l-i-1];
                matrix[j][l-i-1]=temp;
            }
        }
    }
}
```

> 复杂度分析

旋转整个二维数组，时间复杂度O(n * n)

额外使用三个int类型辅助，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Rotate Image.

Memory Usage: 39.9 MB, less than 17.20% of Java online submissions for Rotate Image.
