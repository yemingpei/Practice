### LeetCode-offer-49

> 题目链接

[LeetCode-offer-49](https://leetcode-cn.com/problems/chou-shu-lcof/)

> 思路

动态规划dp[i] = Math.min(Math.min(dpa, dpb), dpc)，a,b,c分别代表乘以2，乘以3，乘以5的指针位置

> 代码

```java
class Solution {
    public int nthUglyNumber(int n) {
        int[] dp = new int[n];
        dp[0] = 1;
        int a = 0,b = 0,c = 0;
        for(int i = 1; i < n; i++){
            int dpa = dp[a] * 2;
            int dpb = dp[b] * 3;
            int dpc = dp[c] * 5;
            dp[i] = Math.min(Math.min(dpa, dpb), dpc);
            if(dp[i] == dpa) a++;
            if(dp[i] == dpb) b++;
            if(dp[i] == dpc) c++;
        }
        return dp[n - 1];
    }
}
```

> 复杂度分析

循环n次，时间复杂度O(n)

额外使用数组来辅助记录结果，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.17%的用户

内存消耗：37.6 MB, 在所有 Java 提交中击败了40.83%的用户
