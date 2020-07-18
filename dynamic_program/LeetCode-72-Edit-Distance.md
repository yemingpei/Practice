### LeetCode-72-Edit-Distance

> 题目链接

[LeetCode-72-Edit-Distance](https://leetcode.com/problems/edit-distance/)

> 思路

由word1推算word2，动态规划公式为dp[i][j] = 1 + Math.min(Math.min(minDistanceRecur(word1, word2, dp, i-1, j), minDistanceRecur(word1, word2, dp, i, j-1)),minDistanceRecur(word1, word2, dp, i-1, j-1))

> 代码

```java
class Solution {
   public int minDistance(String word1, String word2) {
        int[][] dp = new int[word1.length()][word2.length()];
        return minDistanceRecur(word1, word2, dp, word1.length()-1, word2.length()-1);
    }
    public static int minDistanceRecur(String word1, String word2, int[][] dp, int i, int j)    {
        if(i<0 && j<0){
            return 0;
        }
        if(i<0 || j<0){
            return i<0 ? j+1 : i+1;
        }
        if(dp[i][j]!=0){
            return dp[i][j];
        }
        
        if(word1.charAt(i) == word2.charAt(j)){
            dp[i][j] = minDistanceRecur(word1, word2, dp, i-1, j-1);
        } else {        
            dp[i][j] = 1 + Math.min(Math.min(minDistanceRecur(word1, word2, dp, i-1, j), minDistanceRecur(word1, word2, dp, i, j-1)),minDistanceRecur(word1, word2, dp, i-1, j-1)) ;
        }
        return dp[i][j];
    }
}
```

> 复杂度分析

需要推算二维数组的值，时间复杂度O(m * n)

额外使用大小是m * n的二维数组来保存，空间复杂度O(m * n)

> 总结

Runtime: 3 ms, faster than 99.67% of Java online submissions for Edit Distance.

Memory Usage: 40.3 MB, less than 7.51% of Java online submissions for Edit Distance.
