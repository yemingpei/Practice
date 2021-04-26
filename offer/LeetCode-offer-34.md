### LeetCode-offer-34

> 题目链接

[LeetCode-offer-34](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

> 思路

遍历路径，用回溯法，组装数据，输出所有符合的值

> 代码

```java
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int target) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        if(root != null) calculate(result, list, 0, target, root);
        return result;
    }
    public void calculate(List<List<Integer>> result, List<Integer> list, int sum, int target, TreeNode node){
        list.add(node.val);
        int count = sum + node.val;
        if(count == target && node.left == null && node.right == null) result.add(new ArrayList<>(list));
        else {
            if(node.left != null) calculate(result, list, count, target, node.left);
            if(node.right != null) calculate(result, list, count, target, node.right);
        }
        list.remove(list.size() - 1);
    }
}
```

> 复杂度分析

每个点都要遍历到,输出合适的路径，时间复杂度O(n)

额外使用list辅助，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.7 MB, 在所有 Java 提交中击败了69.65%的用户
