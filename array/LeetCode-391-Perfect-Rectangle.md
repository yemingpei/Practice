### LeetCode-391-Perfect-Rectangle

> 题目链接

[LeetCode-391-Perfect-Rectangle](https://leetcode.com/problems/perfect-rectangle/)

> 思路

如果解该题需要遍历所有的小矩形，遍历过程中需要等到完美矩形的左下角和右上角坐标、矩形面积之和，以及顶点的出现情况，最后，判断小矩形面积之和和完美矩形面积之和是否相等，集合中是否只包含4个顶点且是完美矩形的四个顶点，只有这两个条件同时满足才能构成完美矩形。

> 代码

```java
class Solution {
    public boolean isRectangleCover(int[][] rectangles) {
        if (rectangles == null || rectangles.length == 0 || rectangles[0].length == 0) return false;
        Set<int[]> set = new TreeSet<>((int[] a, int[] b) -> {
            if (a[3] <= b[1]) return -1;
            else if (a[1] >= b[3]) return 1;
            else if (a[2] <= b[0]) return -1;
            else if (a[0] >= b[2]) return 1;
            else return 0;    
        });
        int area = 0;
        int up = Integer.MIN_VALUE;
        int down = Integer.MAX_VALUE;
        int left = Integer.MAX_VALUE;
        int right = Integer.MIN_VALUE;
        for (int[] rect: rectangles) {
            area += (rect[2] - rect[0]) * (rect[3] - rect[1]);
            up = Math.max(up, rect[3]);
            down = Math.min(down, rect[1]);
            left = Math.min(left, rect[0]);
            right = Math.max(right, rect[2]);
            if (!set.add(rect)) return false;
        }
        if ((up - down) * (right - left) != area) return false;
        else return true;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要使用treeSet来辅助，空间复杂度O(n)

> 总结

Runtime: 12 ms, faster than 100.00% of Java online submissions for Perfect Rectangle.

Memory Usage: 46.8 MB, less than 94.65% of Java online submissions for Perfect Rectangle.
