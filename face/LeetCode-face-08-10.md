### LeetCode-face-08-10

> 题目链接

[LeetCode-face-08-10](https://leetcode-cn.com/problems/color-fill-lcci/)

> 思路

从起点坐标出发，不断寻找target颜色，把这个颜色改成新的颜色

> 代码

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        if(image[sr][sc] == newColor) return image;
        colorFill(image, sr, sc, image[sr][sc], newColor);
        return image;
    }

    public void colorFill(int[][] image, int x, int y, int target, int newColor){
        image[x][y] = newColor;
        if(x > 0 && image[x - 1][y] == target) colorFill(image, x - 1, y, target, newColor);
        if(y > 0 && image[x][y - 1] == target) colorFill(image, x, y - 1, target, newColor);
        if(x < image.length - 1 && image[x + 1][y] == target) colorFill(image, x + 1, y, target, newColor);
        if(y < image[0].length - 1 && image[x][y + 1] == target) colorFill(image, x, y + 1, target, newColor);
    }
}
```

> 复杂度分析

需要遍历相邻的有颜色的点，时间复杂度O(nm) 

递归栈深度为nm，空间复杂度O(nm)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了92.39%的用户
