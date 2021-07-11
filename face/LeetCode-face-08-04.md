### LeetCode-face-08-04

> 题目链接

[LeetCode-face-08-04](https://leetcode-cn.com/problems/power-set-lcci/)

> 思路

经典的回溯法，不断递归，寻找全部有可能的组合

> 代码

```java
class Solution {
    List<List<Integer>> res = new ArrayList<>();
    public List<List<Integer>> subsets(int[] nums) {
        backtrack(nums, 0, new ArrayList<>());
        return res;
    }
    private void backtrack(int[] nums, int index, List<Integer> list) {
        res.add(new ArrayList<>(list));
        for (int i = index; i < nums.length; i++) {
            list.add(nums[i]);
            backtrack(nums, i + 1, list);
            list.remove(list.size() - 1);
        }
    }
}
```

> 复杂度分析

全部组合，时间复杂度O(2 ^ n) 

额外使用list变量，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了98.38%的用户
