### LeetCode-593-valid-square

> 题目链接

[LeetCode-593-valid-square](https://leetcode-cn.com/problems/valid-square/)

> 思路

检索是否存在四个等腰三角形

> 代码

```java
public class Solution {
    public boolean validSquare(int[] p1, int[] p2, int[] p3, int[] p4) {
        return isRightTriangle(p1, p2, p3) && isRightTriangle(p1, p2, p4) && isRightTriangle(p1, p3, p4) && isRightTriangle(p2, p3, p4);
    }

    public boolean isRightTriangle(int[] p1, int[]p2, int[] p3){
        int d1 = (p1[0] - p2[0]) * (p1[0] - p2[0]) + (p1[1] - p2[1]) * (p1[1] - p2[1]);
        int d2 = (p2[0] - p3[0]) * (p2[0] - p3[0]) + (p2[1] - p3[1]) * (p2[1] - p3[1]);
        int d3 = (p3[0] - p1[0]) * (p3[0] - p1[0]) + (p3[1] - p1[1]) * (p3[1] - p1[1]);
        if(d1 > d2 && d2 == d3 && d2 + d3 == d1 ||
            d2 > d1 && d1 == d3 && d1 + d3 == d2 ||
            d3 > d1 && d1 == d2 && d1 + d2 == d3){
            return true;
        }
        return false;
    }
}
```

> 复杂度分析

计算三条边的关系，时间复杂度O(1)

额外使用固定次数的计算，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.3 MB, 在所有 Java 提交中击败了42.20%的用户
