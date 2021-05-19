### LeetCode-offer-60

> 题目链接

[LeetCode-offer-60](https://leetcode-cn.com/problems/nge-tou-zi-de-dian-shu-lcof/)

> 思路

动态规划,f(n,x)=i=1∑6​f(n−1,x−i)×61​

> 代码

```java
class Solution {
    public double[] dicesProbability(int n) {
        double[] dp = new double[6];
        Arrays.fill(dp, 1.0 / 6.0);
        for (int i = 2; i <= n; i++) {
            double[] tmp = new double[5 * i + 1];
            for (int j = 0; j < dp.length; j++) {
                for (int k = 0; k < 6; k++) {
                    tmp[j + k] += dp[j] / 6.0;
                }
            }
            dp = tmp;
        }
        return dp;
    }
}
```

> 复杂度分析

双重遍历，时间复杂度O(n ^ 2)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了37.70%的用户
