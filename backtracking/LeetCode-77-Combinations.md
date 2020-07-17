### LeetCode-77-Combinations

> 题目链接

[LeetCode-77-Combinations](https://leetcode.com/problems/combinations/)

> 思路

回溯法，当个数为k的时候输出

> 代码

```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> ret = new ArrayList<>();
        List<Integer> holder = new ArrayList<>();
        backtracking(ret, holder, 1, n, k);
        return ret;
    }
    private void backtracking(List<List<Integer>> ret, List<Integer> holder, int start, int n, int k){
        if(k==0){
            ret.add(new ArrayList<>(holder));
            return;
        }
        for(int i= start; i<= n-(k-1); i++){
            holder.add(i);
            backtracking(ret, holder, i+1,n,k-1);
            holder.remove(holder.size()-1);            
        }
    }
}
```

> 复杂度分析

从每一行开始，不断向下推理，时间复杂度O((n!/(N−k)!k!)

额外使用有list，空间复杂度O(n ^ 2)

> 总结

Runtime: 3 ms, faster than 90.58% of Java online submissions for Combinations.

Memory Usage: 40.8 MB, less than 57.36% of Java online submissions for Combinations.
