### LeetCode-offer-57-I

> 题目链接

[LeetCode-offer-57-I](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

> 思路

寻找合适的和，从头尾节点开始，如果比target大，则右边界往左移动，相等则输出，否则，左边界右移动

> 代码

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int i = 0, j = nums.length - 1;
        while(i < j){
            if(nums[i] + nums[j] < target) i++;
            else if(nums[i] + nums[j] > target) j--;
            else return new int[]{nums[i], nums[j]};
        }
        return new int[]{};
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用左右的边界标记，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.83%的用户

内存消耗：55.2 MB, 在所有 Java 提交中击败了82.18%的用户
