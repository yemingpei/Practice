### LeetCode-face-16-03

> 题目链接

[LeetCode-face-16-03](https://leetcode-cn.com/problems/intersection-lcci/)

> 思路

先比较斜率是否相同，相同就有重叠和平行两种情况，否则就是看是否相交

> 代码

```java
class Solution {
    double[] ans = new double[0];

    public double[] intersection(int[] start1, int[] end1, int[] start2, int[] end2) {
        int x1 = start1[0], y1 = start1[1];
        int x2 = end1[0], y2 = end1[1];
        int x3 = start2[0], y3 = start2[1];
        int x4 = end2[0], y4 = end2[1];

        if ((y4 - y3) * (x2 - x1) == (y2 - y1) * (x4 - x3)) {
            if ((y2 - y1) * (x3 - x1) == (y3 - y1) * (x2 - x1)) {
                if (inside(x1, y1, x2, y2, x3, y3))  update(x3, y3);
                if (inside(x1, y1, x2, y2, x4, y4))  update(x4, y4);
                if (inside(x3, y3, x4, y4, x1, y1))  update(x1, y1);
                if (inside(x3, y3, x4, y4, x2, y2))  update(x2, y2);
            }
        } else {
            double t1 = (double) (x3 * (y4 - y3) + y1 * (x4 - x3) - y3 * (x4 - x3) - x1 * (y4 - y3)) / ((x2 - x1) * (y4 - y3) - (x4 - x3) * (y2 - y1));
            double t2 = (double) (x1 * (y2 - y1) + y3 * (x2 - x1) - y1 * (x2 - x1) - x3 * (y2 - y1)) / ((x4 - x3) * (y2 - y1) - (x2 - x1) * (y4 - y3));
            if (t1 >= 0.0 && t1 <= 1.0 && t2 >= 0.0 && t2 <= 1.0) ans = new double[]{x1 + t1 * (x2 - x1), y1 + t1 * (y2 - y1)};
        }
        return ans;
    }
    
    public boolean inside(int x1, int y1, int x2, int y2, int xk, int yk) {
        return (x1 == x2 || (Math.min(x1, x2) <= xk && xk <= Math.max(x1, x2))) && (y1 == y2 || (Math.min(y1, y2) <= yk && yk <= Math.max(y1, y2)));
    }

    public void update(double xk, double yk) {
        if (ans.length == 0 || xk < ans[0] || (xk == ans[0] && yk < ans[1])) ans = new double[]{xk, yk};
    }
}
```

> 复杂度分析

公式计算，时间复杂度O(1)

额外使用int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.2 MB, 在所有 Java 提交中击败了83.15%的用户
