### LeetCode-218-The-Skyline-Problem

> 题目链接

[LeetCode-218-The-Skyline-Problem](https://leetcode.com/problems/the-skyline-problem/)

> 思路

分左右部分开始递归，然后合并，需要比较左右部分的高度，用于合并，处理边界的高低，合并点和剔除被掩盖的点

> 代码

```java
class Solution {
    public List<List<Integer>> getSkyline(int[][] buildings) {
        int len = buildings.length;
        if (len == 0) return new ArrayList<>();
        return segment(buildings, 0, len - 1);
    }

    private List<List<Integer>> segment(int[][] buildings, int l, int r) {
        List<List<Integer>> res = new ArrayList<>();
        if (l == r) {
            res.add(Arrays.asList(buildings[l][0], buildings[l][2]));
            res.add(Arrays.asList(buildings[l][1], 0));
            return res;
        }
        int mid = l + (r - l) / 2;
        List<List<Integer>> left = segment(buildings, l, mid);
        List<List<Integer>> right = segment(buildings, mid + 1, r);
        int m = 0, n = 0;
        int lpreH = 0, rpreH = 0;
        int leftX, leftY, rightX, rightY;
        while (m < left.size() || n < right.size()) {
            if (m >= left.size()) res.add(right.get(n++));
            else if (n >= right.size()) res.add(left.get(m++));
            else {
                leftX = left.get(m).get(0);
                leftY = left.get(m).get(1);
                rightX = right.get(n).get(0);
                rightY = right.get(n).get(1);
                if (leftX < rightX) {
                   if (leftY > rpreH) res.add(left.get(m));
                   else if (lpreH > rpreH) res.add(Arrays.asList(leftX, rpreH));
                    lpreH = leftY;
                    m++;
                } else if (leftX > rightX) {
                   if (rightY > lpreH) res.add(right.get(n));
                   else if (rpreH > lpreH) res.add(Arrays.asList(rightX, lpreH));
                    rpreH = rightY;
                    n++;
                } else {
                  if (leftY >= rightY && leftY != (lpreH > rpreH ? lpreH : rpreH)) res.add(left.get(m));
                    else if (leftY <= rightY && rightY != (lpreH > rpreH ? lpreH : rpreH)) res.add(right.get(n));
                    lpreH = leftY;
                    rpreH = rightY;
                    m++;
                    n++;
                }
            }
        }
        return res;
    }
}
```

> 复杂度分析

分治，使用了归并，时间复杂度O(nlgn)

无额外使用常量来保存，栈的高度为lgH，H为数组的高数，空间复杂度O(lgH)

> 总结

Runtime: 4 ms, faster than 99.25% of Java online submissions for The Skyline Problem.

Memory Usage: 41.7 MB, less than 95.82% of Java online submissions for The Skyline Problem.
