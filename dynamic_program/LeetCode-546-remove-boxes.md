### LeetCode-546-remove-boxes

> 题目链接

[LeetCode-546-remove-boxes](https://leetcode-cn.com/problems/remove-boxes/)

> 思路

动态规划公式dp[l][r][k] = Math.max(dp[l][r][k], calculatePoints(boxes, l, i, k1 + 1) + calculatePoints(boxes, i + 1, r1 - 1, 0))，三维数组l和r代表区间，k代表剩余数字重复的个数

> 代码

```java
class Solution {
    int[][][] dp;
    public int removeBoxes(int[] boxes) {
        int length = boxes.length;
        dp = new int[length][length][length];
        return calculatePoints(boxes, 0, length - 1, 0);
    }
    public int calculatePoints(int[] boxes, int l, int r, int k) {
        if (l > r) {
            return 0;
        }
        if (dp[l][r][k] == 0) {
            int r1 = r, k1 = k;
            while (r1 > l && boxes[r1] == boxes[r1 - 1]) {
                r1--;
                k1++;
            }
            dp[l][r][k] = calculatePoints(boxes, l, r1 - 1, 0) + (k1 + 1) * (k1 + 1);
            for (int i = l; i < r1; i++) {
                if (boxes[i] == boxes[r1]) {
                    dp[l][r][k] = Math.max(dp[l][r][k], calculatePoints(boxes, l, i, k1 + 1) + calculatePoints(boxes, i + 1, r1 - 1, 0));
                }
            }
        }
        return dp[l][r][k];
    }
}
```

> 复杂度分析

三维遍历嵌套深度n的检索，时间复杂度O(n ^ 4)

额外使用三维数组，空间复杂度O(n ^ 3)

> 总结

执行用时：37 ms, 在所有 Java 提交中击败了83.05%的用户

内存消耗：48.3 MB, 在所有 Java 提交中击败了25.42%的用户
