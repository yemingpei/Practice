### LeetCode-46-Permutations

> 题目链接

[LeetCode-46-Permutations](https://leetcode.com/problems/permutations/)

> 思路

回溯法，通过不断交换位置，完成全排列

> 代码

```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList();
        List<Integer> numsList = new ArrayList();
        for(int e : nums) numsList.add(e);
        permutation(result, numsList, 0);
        return result;
    }
    private void permutation(List<List<Integer>> result, List<Integer> nums, int li){
    	if(li == nums.size()-1) result.add(new ArrayList(nums));
    	for(int i = li; i < nums.size(); ++i) {
    		Collections.swap(nums, li, i);
    		permutation(result, nums, li+1);
    		Collections.swap(nums, i, li);
    	}
    }
}
```

> 复杂度分析

全排列，时间复杂度O(n!)

额外使用有list，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 91.83% of Java online submissions for Permutations.

Memory Usage: 39.9 MB, less than 38.08% of Java online submissions for Permutations.
