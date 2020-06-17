### LeetCode-40-Combination-Sum-II

> 题目链接

[LeetCode-40-Combination-Sum-II](https://leetcode.com/problems/combination-sum-ii/)

> 思路

回溯法，同[LeetCode-39-Combination-Sum](https://leetcode.com/problems/combination-sum/)，先做排序，方便去重，然后比较前后位置是否一致，一致则不再往下走

> 代码

```java
class Solution {
    List<List<Integer>> result;
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
      result = new ArrayList<>();
      Arrays.sort(candidates);
      findRes(candidates, target, result, new ArrayList<>(), 0);
      return result;
	 }
    public void findRes(int[] can, int tar, List<List<Integer>> res, List<Integer> list, int low){
        if(tar == 0){
            res.add(new ArrayList<>(list));
            return;
        }
        for(int i = low; i < can.length; ++i){
        	if(i > low && can[i-1] == can[i]) continue;
            if(can[i] <= tar){
                list.add(can[i]);
                findRes(can, tar-can[i], res, list, i+1);
                list.remove(list.size()-1);
            }else return;
        }
    }
}
```

> 复杂度分析

每个数只有选和不选两种情况，形成组合，时间复杂度O(2 ^ n)

额外使用有数组list，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 98.36% of Java online submissions for Combination Sum II.

Memory Usage: 39.2 MB, less than 97.29% of Java online submissions for Combination Sum II.
