### LeetCode-135-Candy

> 题目链接

[LeetCode-135-Candy](https://leetcode.com/problems/candy/)

> 思路

先初始化整个数组，然后左边开始遍历，遇到大的就前面的加1，然后从右边开始遍历，遇到大的，再加1，如果后者比前者大，在最后遍历相加得到结果

> 代码

```java
class Solution {
    public int candy(int[] ratings) {
        if (ratings == null || ratings.length == 0) {
            return 0;
        }
        int[] res = new int[ratings.length];
        for(int i = 0; i < res.length; i++) {
            res[i] = 1;
        }
        for(int i = 1; i < res.length; i++) {
            if (ratings[i] > ratings[i-1]) {
                res[i] = res[i-1] + 1;
            }
        }
        for(int i = res.length-2; i >= 0; i--) {
            if (ratings[i] > ratings[i+1]) {
                res[i] = Math.max(res[i], res[i+1]+1);
            }
        }
        int sum = 0;
        for(int i = 0; i < ratings.length; i++) {
            sum += res[i];
        }
        return sum;
    }
}
```

> 复杂度分析

for循环遍历了四遍数组，时间复杂度O(n)

额外使用了数组保存，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Candy.

Memory Usage: 40.6 MB, less than 49.89% of Java online submissions for Candy.
