### LeetCode-128-Longest-Consecutive-Sequence

> 题目链接

[LeetCode-128-Longest-Consecutive-Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

> 思路

先保存数组的数，建立hash表，然后开始遍历，通过record.contains(number - 1)来跳过连续序列的值，达到n的效果

> 代码

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> record = new HashSet<>();
        for(int num: nums){
            record.add(num);
        }
        int longest = 0;
        for(int number: nums){
            if(!record.contains(number - 1)){
                int count = 1;
                while(record.contains(++number)){
                    count++;
                }
                longest = Math.max(longest, count);
            }
        }
        return longest;
    }
}
```

> 复杂度分析

第一次遍历，记录set，第二次遍历会跳过连续的序列，确保连续的最多检测两次，用时3n，时间复杂度O(n)

额外使用hashSet来保存数据，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 94.33% of Java online submissions for Longest Consecutive Sequence.

Memory Usage: 40 MB, less than 31.44% of Java online submissions for Longest Consecutive Sequence.
