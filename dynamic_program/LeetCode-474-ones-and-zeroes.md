### LeetCode-474-ones-and-zeroes

> 题目链接

[LeetCode-474-ones-and-zeroes](https://leetcode-cn.com/problems/ones-and-zeroes/)

> 思路

动态规划公式dp[z][o] = Math.max(dp[z][o], dp[z - zero][o - one] + 1)

> 代码

```java
class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        int[][] dp = new int[m + 1][n + 1];
        for(int i = 0; i < strs.length; i++){
            int zero = 0;
            int one = 0;
            for(char c : strs[i].toCharArray()){
                if(c == '0') zero++;
                else one++;
            }
            for(int z = m; z >= zero; z--){
                for(int o = n; o >= one; o--){
                    int last = dp[z - zero][o - one];
                    dp[z][o] = Math.max(dp[z][o], last + 1);
                }
            }
        }
        return dp[m][n];
    }
}
```

> 复杂度分析

三重循环，时间复杂度O(n^3)

额外使用数组，空间复杂度O(nm)

> 总结

执行用时：24 ms, 在所有 Java 提交中击败了99.04%的用户

内存消耗：37.7 MB, 在所有 Java 提交中击败了80.26%的用户
