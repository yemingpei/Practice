### LeetCode-526-beautiful-arrangement

> 题目链接

[LeetCode-526-beautiful-arrangement](https://leetcode-cn.com/problems/beautiful-arrangement/)

> 思路

因为n小于15，利用状态转换dp[s] += dp[s ^ (1 << i)]快速完成转换

> 代码

```java
class Solution {
    public int countArrangement(int n) {
        int state = 1 << n;
        int[] dp = new int[state];
        for(int i = 0; i < n; i++){
            dp[1 << i] = 1;
        }
        for(int s = 1; s < state; s++){
            int num = Integer.bitCount(s);
            for (int i = 0; i < n; i++){
                if ((s & (1 << i)) != 0 && (num % (i + 1) == 0 || (i + 1) % num == 0)){
                    dp[s] += dp[s ^ (1 << i)];
                }
            }
        }
        return dp[state - 1];
    }
}
```

> 复杂度分析

双重循环，时间复杂度O(n * 2 ^ n)

额外使用数组，空间复杂度O(2 ^ n)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了93.83%的用户

内存消耗：35.5 MB, 在所有 Java 提交中击败了43.73%的用户
