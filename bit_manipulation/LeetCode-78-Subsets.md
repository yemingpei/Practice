### LeetCode-78-Subsets

> 题目链接

[LeetCode-78-Subsets](https://leetcode.com/problems/subsets/)

> 思路

因为该题的case的数量不超过32，所以可以使用位运算（真理应该使用回溯），使用nums.length个二进制的数来表示nums.length选或者不选，选则为1，不选为0

> 代码

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        int size = nums.length;
        int count = 1 << size;
        result.add(new ArrayList<>());
        for(int i = 1; i < count; i++){
            List<Integer> list = new ArrayList<>();
            int m = 1;
            for(int j = 0; j < size; j++){
                if ((i & m) != 0) {
                    list.add(nums[j]);
                }
                m = m << 1;
            }
            result.add(list);
        }
        return result;
    }
}
```

> 复杂度分析

子集问题，时间复杂度O(2 ^ n)

额外使用有list来辅助，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Subsets.

Memory Usage: 39.9 MB, less than 38.25% of Java online submissions for Subsets.
