### LeetCode-offer-32-II

> 题目链接

[LeetCode-offer-32-II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

> 思路

先序遍历，完成数组的拼装

> 代码

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if(root != null) printTree(result, 0, root);
        return result;
    }
    public void printTree(List<List<Integer>> result, int position, TreeNode root){
        if(position == result.size()) result.add(new ArrayList<>());
        result.get(position).add(root.val);
        if(root.left != null) printTree(result, position + 1, root.left);
        if(root.right != null) printTree(result, position + 1, root.right);
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用其他结构，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了54.74%的用户
