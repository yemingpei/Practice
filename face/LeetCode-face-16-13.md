### LeetCode-face-16-13

> 题目链接

[LeetCode-face-16-13](https://leetcode-cn.com/problems/bisect-squares-lcci/)

> 思路

先找出正方形的中点，然后计算两个点的线段，在寻找距离最长的两个点

> 代码

```java
class Solution {
    public double[] cutSquares(int[] square1, int[] square2) {
        double x1 = square1[0] + square1[2] / 2.0;
        double y1 = square1[1] + square1[2] / 2.0;
        double x2 = square2[0] + square2[2] / 2.0;
        double y2 = square2[1] + square2[2] / 2.0;
        double xs, ys, xe, ye;
        if(x1 == x2) {
            xs = x1;
            ys = Math.min(square1[1], square2[1]);
            xe = x1;
            ye = Math.max(square1[1] + square1[2], square2[1] + square2[2]);
            return new double[]{xs, ys, xe, ye};
        }
        double k = (y2 - y1) / (x2 - x1);
        double b = y1 - k * x1;
        if(Math.abs(k) < 1) {
            xs = Math.min(square1[0], square2[0]);
            ys = k * xs + b;
            xe = Math.max(square1[0] + square1[2], square2[0] + square2[2]);
            ye = k * xe + b;
        }else {
            ys = Math.min(square1[1], square2[1]);
            xs = (ys - b) / k;
            ye = Math.max(square1[1] + square1[2], square2[1] + square2[2]);
            xe = (ye - b) / k;
            if(xs >= xe) {
                double temp = ys;
                ys = ye;
                ye = temp;
                temp = xs;
                xs = xe;
                xe = temp;
            }
        }
        return new double[] {xs, ys, xe, ye};
    }
}
```

> 复杂度分析

根据公式计算，时间复杂度O(1)

额外使用double变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.2 MB, 在所有 Java 提交中击败了84.03%的用户
