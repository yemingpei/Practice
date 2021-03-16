### LeetCode-offer-04

> 题目链接

[LeetCode-offer-04](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

> 思路

左下角开始搜索，如果比target大，就往上移动，否则往右移动，相等提前退出，超过边界则无法找到该值

> 代码

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        int row = matrix.length;
        if(row == 0) return false;
        int column = matrix[0].length;
        if(column == 0) return false;
        int n = row - 1, m = 0;
        while(n >= 0 && m < column){
            int number = matrix[n][m];
            if(number == target) return true;
            else if(number < target) m++;
            else n--;
        }
        return false;
    }
}
```

> 复杂度分析

从左下角开始搜寻，时间复杂度O(n + m)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：44.1 MB, 在所有 Java 提交中击败了66.07%的用户

