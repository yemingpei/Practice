### LeetCode-face-08-13

> 题目链接

[LeetCode-face-08-13](https://leetcode-cn.com/problems/pile-box-lcci/)

> 思路

先排序，然后用动态规划，公式dp[i] = Math.max(dp[i], dp[j] + box[i - 1][2])来规划箱子是否能套住

> 代码

```java
class Solution {
    public int pileBox(int[][] box) {
        Arrays.sort(box, (a, b) -> {
            if (a[0] != b[0]) {
                return a[0] - b[0];
            } else {
                return b[1] - a[1];
            }
        });
        int m = box.length;
        int max = 0;
        int[] dp = new int[m + 1];
        for (int i = 1; i < m + 1; i++) {
            dp[i] = box[i - 1][2];
            for (int j = 1; j < i; j++) {
                if (box[j - 1][1] < box[i - 1][1] && box[j - 1][2] < box[i - 1][2]) {
                    dp[i] = Math.max(dp[i], dp[j] + box[i - 1][2]);
                }
            }
            max = Math.max(max, dp[i]);
        }
        return max;
    }
}
```

> 复杂度分析

双重遍历，时间复杂度O(n ^ 2) 

需要使用数组辅助，空间复杂度O(n)

> 总结

执行用时：29 ms, 在所有 Java 提交中击败了88.01%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了73.98%的用户
