### LeetCode-583-delete-operation-for-two-strings

> 题目链接

[LeetCode-583-delete-operation-for-two-strings](https://leetcode-cn.com/problems/delete-operation-for-two-strings/)

> 思路

动态规划result[j] = Math.min(left, result[j]) + 1；result[j] = result[j - 1]（旧值）

> 代码

```java
class Solution {
    public int minDistance(String word1, String word2) {
        int n = word1.length();
        int m = word2.length();
        int[] result = new int[m + 1];
        for(int i = 1; i <= m; i++){
            result[i] = i;
        }
        for(int i = 1; i <= n; i++){
            int left = i;
            int last = result[0];
            char c1 = word1.charAt(i - 1);
            for(int j = 1; j <= m; j++){
                int number = result[j];
                char c2 = word2.charAt(j - 1);
                if(c2 == c1) result[j] = last;
                else result[j] = Math.min(left, result[j]) + 1;
                left = result[j];
                last = number;
            }
            result[0] = i;
        }
        return result[m];
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(nm)

额外使用数组，空间复杂度O(m)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了99.17%的用户

内存消耗：38.5 MB, 在所有 Java 提交中击败了93.59%的用户
