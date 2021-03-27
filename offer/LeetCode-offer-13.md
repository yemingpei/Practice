### LeetCode-offer-13

> 题目链接

[LeetCode-offer-13](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

> 思路

能否达到该位置，由该位置的前一个或者上一个为true决定，则有flag[i][j] = flag[i - 1][j] || flag[i][j - 1],可以优化空间为O(n)

> 代码

```java
class Solution {
    public int movingCount(int m, int n, int k) {
        boolean[] flag = new boolean[n];
        int count = 1;
        flag[0] = true;
        for(int j = 1; j < n; j++){
            if(flag[j - 1] && getSum(j) <= k){
                flag[j] = true;
                count++;
            }
        }
        for(int i = 1; i < m; i++){
            int start = getSum(i);
            for(int j = 0; j < n; j++){
                if((flag[j] || (j > 0 && flag[j - 1])) && start + getSum(j) <= k){
                    flag[j] = true;
                    count++;
                }else flag[j] = false;
            }
        }
        return count;
    }
    public int getSum(int i){
        int number = 0;
        while(i != 0){
            number += i % 10;
            i /= 10;
        }
        return number;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(n ^ 2)

额外使用布尔数组，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.27%的用户

内存消耗：40.2 MB, 在所有 Java 提交中击败了66.80%的用户

