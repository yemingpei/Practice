### LeetCode-219-Contains-Duplicate-II

> 题目链接

[LeetCode-219-Contains-Duplicate-II](https://leetcode.com/problems/contains-duplicate-ii/)

> 思路

如果HashMap集合里面没有该数字或者相隔的位置超过k，就保存数组的数和对应的position，否则返回true

> 代码

```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>(nums.length);
        for(int i = 0; i < nums.length; i++){
            if(map.containsKey(nums[i]) && i - map.get(nums[i]) <= k) return true;
            map.put(nums[i], i);
        }
        return false;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用HashMap来保存数据，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 91.73% of Java online submissions for Contains Duplicate II.

Memory Usage: 44.9 MB, less than 10.65% of Java online submissions for Contains Duplicate II.
