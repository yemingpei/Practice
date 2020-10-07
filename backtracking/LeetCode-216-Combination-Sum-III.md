### LeetCode-216-Combination-Sum-III

> 题目链接

[LeetCode-216-Combination-Sum-III](https://leetcode.com/problems/combination-sum-iii/)

> 思路

回溯，寻找和为n的组合，典型的回溯问题，需要剪枝，list.size() == k，sum > n 两个条件提前退出

> 代码

```java
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> result = new ArrayList<>();
        addNums(result, new ArrayList<>(), k, n, 0, 0);
        return result;
    }
    private void addNums(List<List<Integer>> result, List<Integer> list,int k, int n, int sum, int number){
        if(list.size() == k){
            if(sum == n) result.add(new ArrayList<>(list));
            return;
        }
        for(int i = number + 1; i < 10; i++){
            int pre = sum + i;
            if(pre > n) break;
            list.add(i);
            addNums(result, list, k, n, pre, i);
            list.remove(list.size() - 1);
        }
    }
}
```

> 复杂度分析

寻找k个数的组合，时间复杂度O(k!)

保存单个答案的数组，空间复杂度O(k)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Combination Sum III.

Memory Usage: 36.5 MB, less than 96.18% of Java online submissions for Combination Sum III.
