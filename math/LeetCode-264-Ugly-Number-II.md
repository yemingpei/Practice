### LeetCode-264-Ugly-Number-II

> 题目链接

[LeetCode-264-Ugly-Number-II](https://leetcode.com/problems/ugly-number-ii/)

> 思路

分别用三个position来代表每个因子的初始位置，然后比较相乘后，哪个比较小，最小的就是下一个丑数。

> 代码

```java
class Solution {
    public int nthUglyNumber(int n) {
        int a = 0, b = 0, c = 0, result = 1;
        int[] nums = new int[1690];
        nums[0] = 1;
        for(int i = 1; i < n; i++){
            result = Math.min(Math.min(nums[a] * 2, nums[b] * 3), nums[c] * 5);
            nums[i] = result;
            if(nums[a] * 2 == result) a++;
            if(nums[b] * 3 == result) b++;
            if(nums[c] * 5 == result) c++;
        }
        return result;
    }
}
```

> 复杂度分析

最多遍历1690次，时间复杂度O(1)

数组长度1690，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 96.27% of Java online submissions for Ugly Number II.

Memory Usage: 38.4 MB, less than 5.39% of Java online submissions for Ugly Number II.
