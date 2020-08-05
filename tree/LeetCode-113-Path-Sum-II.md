### LeetCode-113-Path-Sum-II

> 题目链接

[LeetCode-113-Path-Sum-II](https://leetcode.com/problems/path-sum-ii/)

> 思路

遍历路径，用回溯法，组装数据，输出所有符合的值

> 代码

```java
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> result = new ArrayList<>();
        if(root != null)
            addPathSum(result, new ArrayList<>(), root, 0, sum);
        return result;
    }
    public void addPathSum(List<List<Integer>> result, List<Integer> list, TreeNode root, int sum, int target){
        list.add(root.val);
        if(root.left == null && root.right == null){
            if(sum + root.val == target){
                result.add(new ArrayList<>(list));
            }
        }else{
            if(root.left != null)
                addPathSum(result, list, root.left, sum + root.val, target);
            if(root.right != null)
                addPathSum(result, list, root.right, sum + root.val, target);
        }
        list.remove(list.size() - 1);
    }
}
```

> 复杂度分析

每个点都要遍历到,输出合适的路径，时间复杂度O(n)

无额外使用空间，空间复杂度O(lgn)

> 总结

Runtime: 1 ms, faster than 99.89% of Java online submissions for Path Sum II.

Memory Usage: 40 MB, less than 36.49% of Java online submissions for Path Sum II.
