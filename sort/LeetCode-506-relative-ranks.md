### LeetCode-506-relative-ranks

> 题目链接

[LeetCode-506-relative-ranks](https://leetcode-cn.com/problems/relative-ranks/)

> 思路

先排序，然后通过二分查找，来寻找名次

> 代码

```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        String[] result = new String[score.length];
        int[] numbers = Arrays.copyOf(score, score.length);
        Arrays.sort(numbers);
        for(int i = 0; i < result.length; i++){
            int rank = result.length - Arrays.binarySearch(numbers, score[i]);
            if(rank == 1) result[i] = "Gold Medal";
            else if(rank == 2) result[i] = "Silver Medal";
            else if(rank == 3) result[i] = "Bronze Medal";
            else result[i] = Integer.toString(rank);
        }
        return result;
    }
}
```

> 复杂度分析

使用了排序，时间复杂度O(nlogn)

额外使用数组辅助，空间复杂度O(n)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了92.92%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了97.88%的用户
