### LeetCode-367-Valid-Perfect-Square

> 题目链接

[LeetCode-367-Valid-Perfect-Square](https://leetcode.com/problems/valid-perfect-square/)

> 思路

二分查找，不断向平方根靠近

> 代码

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        if(num < 2) return true;
        long left = 1;
        long right = num / 2;
        while(right >= left){
            long mid = (left + right) / 2;
            long count = mid * mid;
            if(count > num)
                right = mid - 1;
            else if(count < num)
                left = mid + 1;
            else
                return true;
        }
        return false;
    }
}
```

> 复杂度分析

二分查找，寻找中间值，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Valid Perfect Square.

Memory Usage: 35.8 MB, less than 38.18% of Java online submissions for Valid Perfect Square.
