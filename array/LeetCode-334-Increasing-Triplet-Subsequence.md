### LeetCode-334-Increasing-Triplet-Subsequence

> 题目链接

[LeetCode-334-Increasing-Triplet-Subsequence](https://leetcode.com/problems/increasing-triplet-subsequence/)

> 思路

```java
例子： 4 5 1 2 7
4
4 5
1 5
1 2
1 2 7
```

寻找一个递增序列，贪心算法，不断压小当前的值，如果相对大的值就添加，到第三个，可以提前跳出

> 代码

```java
class Solution {
    public boolean increasingTriplet(int[] nums) {
        int smal = Integer.MAX_VALUE;
        int big = Integer.MAX_VALUE;
        for(int i : nums){
            if(i <= smal) smal = i;
            else if(i <= big) big = i;
            else return true;
        }
        return false;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要两个常量int来记录递增序列的第一第二个值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Increasing Triplet Subsequence.

Memory Usage: 38.6 MB, less than 88.89% of Java online submissions for Increasing Triplet Subsequence.
