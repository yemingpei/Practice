### LeetCode-face-17-9

> 题目链接

[LeetCode-face-17-9](https://leetcode-cn.com/problems/get-kth-magic-number-lcci/)

> 思路

模拟三个数字在跳，从起点开始，每次只能最小的跳，每个位置都会经历各个因子的乘法

> 代码

```java
class Solution {
    public int getKthMagicNumber(int k) {
        if(k < 1) return -1;
        int[] dp = new int[k];
        int p1 = 0, p2 = 0, p3 = 0;
        dp[0] = 1;
        for(int i = 1; i < k; i++){
            int v1 = dp[p1] * 3, v2 = dp[p2] * 5, v3 = dp[p3] * 7;
            dp[i] = Math.min(v1, Math.min(v2, v3));
            if(v1 == dp[i]) p1++;
            if(v2 == dp[i]) p2++;
            if(v3 == dp[i]) p3++;
        }
        return dp[k - 1];
    }
}
```

> 复杂度分析

遍历两次数组，时间复杂度O(n)

额外使用int数组辅助，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.2 MB, 在所有 Java 提交中击败了65.00%的用户
