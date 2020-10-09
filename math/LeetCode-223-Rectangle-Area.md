### LeetCode-223-Rectangle-Area

> 题目链接

[LeetCode-223-Rectangle-Area](https://leetcode.com/problems/rectangle-area/)

> 思路

先计算重叠的面积，然后两个面积之和，然后再减去重叠的面积

> 代码

```java
class Solution {
    public int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        return (C - A) * (D - B) +
            (G - E) * (H - F) -
            getOverlappingArea(A, B, C, D, E, F, G, H);
    }
    
    public int getOverlappingArea(int A, int B, int C, int D, int E, int F, int G, int H){
        if(A <= E && C <= E) return 0;
        if(A >= G && C >= G) return 0;
        if(B <= F && D <= F) return 0;
        if(B >= H && D >= H) return 0;
        int a = Math.max(A, E);
        int c = Math.min(C, G);
        int b = Math.max(B, F);
        int d = Math.min(D, H);
        return (c -a) * (d - b);
    }
}
```

> 复杂度分析

先计算重叠的面积，然后两个面积之和，然后再减去重叠的面积，时间复杂度O(1)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Rectangle Area.

Memory Usage: 38.1 MB, less than 8.24% of Java online submissions for Rectangle Area.
