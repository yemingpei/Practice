### LeetCode-217-Contains-Duplicate

> 题目链接

[LeetCode-217-Contains-Duplicate](https://leetcode.com/problems/contains-duplicate/)

> 思路

如果set集合里面没有该数字，就保存数组的数，否则返回true

> 代码

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>(nums.length);
        for(int number:nums){
            if(set.contains(number)) return true;
            set.add(number);
        }
        return false;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用hashSet来保存数据，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 75.82% of Java online submissions for Contains Duplicate.

Memory Usage: 45.4 MB, less than 10.60% of Java online submissions for Contains Duplicate.
