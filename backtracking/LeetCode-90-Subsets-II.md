### LeetCode-90-Subsets-II

> 题目链接

[LeetCode-90-Subsets-II](https://leetcode.com/problems/subsets-ii/)

> 思路

回溯法，先做排序，方便去重，然后比较前后位置是否一致，一致则不再往下走

> 代码

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        result.add(new ArrayList<>());
        Arrays.sort(nums);
        for(int i = 0; i < nums.length; i++){
            if(i != 0 && nums[i] == nums[i - 1]) continue;
            addSubsets(result, new ArrayList<>(), nums, i);
        }
        return result;
    }
    public void addSubsets(List<List<Integer>> result, List<Integer> list, int[] nums, int i){
        list.add(nums[i]);
        result.add(new ArrayList<>(list));
        for(int j = i+1; j < nums.length; j++){
            if(j != i +1 && nums[j] == nums[j - 1]) continue;
            addSubsets(result, list, nums, j);
        }
        list.remove(list.size() - 1);
    }
}
```

> 复杂度分析

最坏情况，没有重复的数字，每个数只有选和不选两种情况，形成组合，时间复杂度O(2 ^ n)

额外使用有数组list，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.89% of Java online submissions for Subsets II.

Memory Usage: 40 MB, less than 13.75% of Java online submissions for Subsets II.
