### LeetCode-287-Find-the-Duplicate-Number

> 题目链接

[LeetCode-287-Find-the-Duplicate-Number](https://leetcode.com/problems/find-the-duplicate-number/)

> 思路

Floyd 判圈算法，慢指针走一步，快指针走两步，走的方式一致，快指针和慢指针会相遇，然后一个从起点出发，一个从相遇点出发，相同步数相遇，则是环的入口，即重复点

> 代码

```java
class Solution {
    public int findDuplicate(int[] nums) {
        int slow = nums[0];
        int fast = nums[nums[0]];
        while(slow != fast){
            slow = nums[slow];
            fast = nums[nums[fast]];
        }
        slow = 0;
        while(slow != fast){
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
}
```

> 复杂度分析

遍历数组,寻找环，时间复杂度O(n)

需要两个常量int来记录slow和fast，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Find the Duplicate Number.

Memory Usage: 38.9 MB, less than 77.92% of Java online submissions for Find the Duplicate Number.
