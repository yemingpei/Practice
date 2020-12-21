### LeetCode-374-Guess-Number-Higher-or-Lower

> 题目链接

[LeetCode-374-Guess-Number-Higher-or-Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)

> 思路

二分查找，不断向pick的数字靠近

> 代码

```java
public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int left = 1;
        int right = n;
        while(right > left){
            int mid = left + ((right - left) >> 1);
            if(guess(mid) > 0) left = mid + 1;
            else right = mid;
        }
        return right;
    }
}
```

> 复杂度分析

二分查找，寻找中间值，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Guess Number Higher or Lower.

Memory Usage: 35.5 MB, less than 81.66% of Java online submissions for Guess Number Higher or Lower.
