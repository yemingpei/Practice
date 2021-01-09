### LeetCode-377-Combination-Sum-IV

> 题目链接

[LeetCode-377-Combination-Sum-IV](https://leetcode.com/problems/combination-sum-iv/)

> 思路

典型的背包问题，target可以通过comb[i] += comb[i - nums[j]]，comb[i - nums[j]]加上i来获得target的其中一个组成

> 代码

```java
class Solution {
    public int combinationSum4(int[] nums, int target) {
        int[] comb = new int[target + 1];
        comb[0] = 1;
        for (int i = 1; i < comb.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                if (i >= nums[j]) {
                    comb[i] += comb[i - nums[j]];
                }
            }
        }
        return comb[target];
    }
}
```

> 复杂度分析

双循环遍历对应的target和nums，时间复杂度O(n * m)

额外使用int的数组来辅助，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 81.57% of Java online submissions for Combination Sum IV.

Memory Usage: 36.4 MB, less than 69.57% of Java online submissions for Combination Sum IV.
