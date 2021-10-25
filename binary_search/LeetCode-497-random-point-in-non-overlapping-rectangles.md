### LeetCode-497-random-point-in-non-overlapping-rectangles

> 题目链接

[LeetCode-497-random-point-in-non-overlapping-rectangles](https://leetcode-cn.com/problems/random-point-in-non-overlapping-rectangles/)

> 思路

利用二分法确认随机的点在哪个位置上

> 代码

```java
class Solution {
    int[][] rects;
    List<Integer> psum = new ArrayList<>();
    int tot = 0;
    Random rand = new Random();

    public Solution(int[][] rects) {
        this.rects = rects;
        for (int[] x : rects){
            tot += (x[2] - x[0] + 1) * (x[3] - x[1] + 1);
            psum.add(tot);
        }
    }

    public int[] pick() {
        int targ = rand.nextInt(tot);

        int lo = 0;
        int hi = rects.length - 1;
        while (lo != hi) {
            int mid = (lo + hi) / 2;
            if (targ >= psum.get(mid)) lo = mid + 1;
            else hi = mid;
        }

        int[] x = rects[lo];
        int width = x[2] - x[0] + 1;
        int height = x[3] - x[1] + 1;
        int base = psum.get(lo) - width * height;
        return new int[]{x[0] + (targ - base) % width, x[1] + (targ - base) / width};
    }
}
```

> 复杂度分析

使用二分法确认点，时间复杂度O(logn)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：59 ms, 在所有 Java 提交中击败了71.43%的用户

内存消耗：44.2 MB, 在所有 Java 提交中击败了97.62%的用户
