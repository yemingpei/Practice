### LeetCode-face-17-23

> 题目链接

[LeetCode-face-17-23](https://leetcode-cn.com/problems/max-black-square-lcci/)

> 思路

先确定最上和最左两个边界，再递归判断最右和最下边界

> 代码

```java
class Solution {
    public int[] findSquare(int[][] matrix) {
        if(matrix==null||matrix.length==0) return new int[0];
        int[][] rowBlack = new int[matrix.length][matrix[0].length];
        int[][] colBlack = new int[matrix.length][matrix[0].length];
        for(int i=matrix.length-1;i>=0;i--){
            for(int j=matrix[0].length-1;j>=0;j--){
                if(matrix[i][j]==0){
                    rowBlack[i][j] = 1;
                    colBlack[i][j] = 1;
                    if(i<matrix.length-1) colBlack[i][j] += colBlack[i+1][j];
                    if(j<matrix[0].length-1) rowBlack[i][j] += rowBlack[i][j+1];
                }
            }
        }
        int[] res = new int[3];
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix[0].length;j++){
                int len = Math.min(rowBlack[i][j],colBlack[i][j]);
                for(int l = len;l>res[2];l--){
                    if(colBlack[i][j+l-1]>=l&&rowBlack[i+l-1][j]>=l){
                        res[0] = i;
                        res[1] = j;
                        res[2] = l;
                        break;
                    }
                }
            }
        }
        if(res[2]==0) return new int[0];
        return res;
    }
}
```

> 复杂度分析

三重循环，时间复杂度O(n ^ 3)

额外使用二维数组，空间复杂度O(n ^ 2)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：45.9 MB, 在所有 Java 提交中击败了34.38%的用户
