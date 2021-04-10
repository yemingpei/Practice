### LeetCode-offer-29

> 题目链接

[LeetCode-offer-29](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

> 思路

从外环开始打印二维数组，注意边界的判断

> 代码

```java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        int m = matrix.length;
        if(m == 0) return new int[0];
        int n = matrix[0].length;
        if(n == 0) return new int[0];
        int length = m * n;
        int[] result = new int[length];
        int left = 0, right = n -1, top = 0, bottom = m - 1, count = 0;
        while(right >= left || bottom >= top){
            for(int i = left; i <= right; i++){
                result[count++] = matrix[top][i];
            }
            if(count >= length) break;
            top++;
            for(int j = top; j <= bottom; j++){
                result[count++] = matrix[j][right];
            }
            if(count >= length) break;
            right--;
            for(int k = right; k >= left; k--){
                result[count++] = matrix[bottom][k];
            }
            if(count >= length) break;
            bottom--;
            for(int z = bottom; z >= top; z--){
                result[count++] = matrix[z][left];
            }
            if(count >= length) break;
            left++;
        }
        return result;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(mn)

额外使用常数个int变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了97.50%的用户

内存消耗：39.6 MB, 在所有 Java 提交中击败了87.93%的用户
