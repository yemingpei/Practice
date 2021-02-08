### LeetCode-448-Find-All-Numbers-Disappeared-in-an-Array

> 题目链接

[LeetCode-448-Find-All-Numbers-Disappeared-in-an-Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

> 思路

原地修改数组，再遍历，确定不出现的数字

> 代码

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> result = new ArrayList<>();
        int start = 0;
        int end = nums.length;
        while (start < end) {
            int j = nums[start] - 1;
            if (j < end && nums[start] != nums[j]) {
                int temp = nums[start];
                nums[start] = nums[j];
                nums[j] = temp;
            } else {
                start++;
            }
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != i + 1) result.add(i + 1);
        }
        return result;
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

原地修改无额外空间，空间复杂度O(1)。

> 总结

Runtime: 5 ms, faster than 83.19% of Java online submissions for Find All Numbers Disappeared in an Array.

Memory Usage: 48 MB, less than 62.91% of Java online submissions for Find All Numbers Disappeared in an Array.
