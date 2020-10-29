### LeetCode-274-H-Index

> 题目链接

[LeetCode-274-H-Index](https://leetcode.com/problems/h-index/)

> 思路

先统计发布了相同次数的文章有多少篇，大于n就用n来记录，因为h在[1,n]的区间内，然后从大到小来计算h，遍历统计的数组，返回符合的h

> 代码

```java
class Solution {
    public int hIndex(int[] citations) {
        int length = citations.length;
        int[] count = new int[length + 1];
        for(int a : citations){
            count[Math.min(a, length)]++;
        }
        int h = length;
        int sum = count[length];
        while(h > sum){
            h--;
            sum += count[h];
        }
        return h;
    }
}
```

> 复杂度分析

需要遍历一遍数组，在遍历一遍计数数组，时间复杂度O(n)

需要数组来统计发布次数的文章，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for H-Index.

Memory Usage: 36.7 MB, less than 5.81% of Java online submissions for H-Index.
