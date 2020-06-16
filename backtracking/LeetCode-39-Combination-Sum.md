### LeetCode-39-Combination-Sum

> 题目链接

[LeetCode-39-Combination-Sum](https://leetcode.com/problems/combination-sum/)

> 思路

回溯法，记录index的位置，防止重复

> 代码

```java
class Solution {
    public List<List<Integer>> result;
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        result = new ArrayList<>();
        for(int i = 0;i < candidates.length; i++)
           findAllNumber(candidates, target, i, new ArrayList<>());
        return result;
    }
    
    public void findAllNumber(int[] candidates, int target, int index, List<Integer> list){
        int differ = target - candidates[index];
        if(differ > 0){
            for(int i = index;i < candidates.length; i++){
                list.add(candidates[index]);
                findAllNumber(candidates, differ, i, list);
                list.remove(list.size()-1);
            }
        }else if(differ == 0){
            list.add(candidates[index]);
            result.add(new ArrayList(list));
            list.remove(list.size()-1);
        }
    }
}
```

> 复杂度分析

无限个可能，时间复杂度O(length ^ n)

额外使用有数组list，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 78.13% of Java online submissions for Combination Sum.

Memory Usage: 39.3 MB, less than 96.40% of Java online submissions for Combination Sum.
