### LeetCode-47-Permutations-II

> 题目链接

[LeetCode-47-Permutations-II](https://leetcode.com/problems/permutations-ii/)

> 思路

回溯法，思路同[LeetCode-46-Permutations](https://leetcode.com/problems/permutations/)，需要去重，去重条件是交换位置的区间内没有相同的元素

> 代码

```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> result = new ArrayList();
        List<Integer> numsList = new ArrayList();
        for(int e : nums) numsList.add(e);
        permutation(result, numsList, 0);
        return result;
    }
    private void permutation(List<List<Integer>> result, List<Integer> nums, int li){
    	if(li == nums.size()-1) result.add(new ArrayList(nums));
    	for(int i = li; i < nums.size(); ++i) {
            if(canSwap(nums, li, i)){
                Collections.swap(nums, li, i);
                permutation(result, nums, li+1);
                Collections.swap(nums, i, li);
            }
    	}
    }
    private boolean canSwap(List<Integer> nums, int start, int end){
        for(int i = start; i < end; i++)
            if(nums.get(i) == nums.get(end)) return false;
        return true;
    }
}
```

> 复杂度分析

全排列,去重，时间复杂度O(n ^ n)

额外使用有list，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.31% of Java online submissions for Permutations II.

Memory Usage: 39.8 MB, less than 95.74% of Java online submissions for Permutations II.
