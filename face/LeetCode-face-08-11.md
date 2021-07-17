### LeetCode-face-08-11

> 题目链接

[LeetCode-face-08-11](https://leetcode-cn.com/problems/coin-lcci/)

> 思路

F(m) = F(m - 5) + ([m/2] + 1)([(m+1)/2] + 1)

> 代码

```java
class Solution {
    public int waysToChange(int n) {
    int ans = 0;
    n = n / 5;
    while(n >= 0){
        ans = (ans + (int)((long)(n / 2 + 1)*(1 + (n + 1) / 2) % 1000000007))% 1000000007;
        n-=5;
    }
    return ans;
    }
}
```

> 复杂度分析

需要计算n/25次，时间复杂度O(n) 

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.91%的用户

内存消耗：35.1 MB, 在所有 Java 提交中击败了98.79%的用户
