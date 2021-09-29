### LeetCode-464-can-i-win

> 题目链接

[LeetCode-464-can-i-win](https://leetcode-cn.com/problems/can-i-win/)

> 思路

利用动态规划，深度遍历，徐照是否有能必胜的方法

> 代码

```java
class Solution {
    public boolean canIWin(int maxChoosableInteger, int desiredTotal) {
        if(maxChoosableInteger >= desiredTotal) return true;
        int r= 1 + maxChoosableInteger;
        if(r * maxChoosableInteger / 2 < desiredTotal) return false;
        if (maxChoosableInteger % 2 == 1){
            if((desiredTotal - r / 2) % r <= r / 2 && (desiredTotal - r / 2) / r >= 2) return true;
        }else {
            if(desiredTotal % (1 + maxChoosableInteger) == 0) return false;
        }
        return dfs(0, desiredTotal, new Boolean[1 << maxChoosableInteger], maxChoosableInteger);
    }

    private boolean dfs(int state, int desiredTotal, Boolean[] dp, int maxChoosableInteger){
        if(dp[state] != null) return dp[state];
        for(int i = 1; i <= maxChoosableInteger; i++){
            int cur = 1 << (i - 1);
            if((cur & state) != 0) continue;
            if(i >= desiredTotal || !dfs(cur | state, desiredTotal - i, dp, maxChoosableInteger)) return dp[state] = true;
        }
        return dp[state] = false;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：52 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：40.8 MB, 在所有 Java 提交中击败了96.13%的用户
