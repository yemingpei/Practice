### LeetCode-275-H-Index-II

> 题目链接

[LeetCode-275-H-Index-II](https://leetcode.com/problems/h-index-ii/)

> 思路

利用二分法，寻找h满足citations[middle - 1] <= h <= citations[middle] 

> 代码

```java
class Solution {
    public int hIndex(int[] citations) {
        int left = 0;
        int right = citations.length - 1;
        while(right >= left){
            int middle = (right - left) / 2 + left;
            int h = citations.length - middle;
            if(h > citations[middle]) left = middle + 1;
            else if(middle > 0 && h < citations[middle - 1]) right =  middle - 1;
            else return h;
        }
        return 0;
    }
}
```

> 复杂度分析

二分查找，时间复杂度O(lgn)

额外使用int来记录边界，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for H-Index II.

Memory Usage: 45.8 MB, less than 7.51% of Java online submissions for H-Index II.
