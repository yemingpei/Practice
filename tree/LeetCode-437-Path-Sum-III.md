### LeetCode-437-Path-Sum-III

> 题目链接

[LeetCode-437-Path-Sum-III](https://leetcode.com/problems/path-sum-iii/)

> 思路

二叉树从root节点出发，到叶子节点的某一条路径。如果前缀总和currSum，在节点A和节点B处相差target，则位于节点A和节点B之间的元素之和是target。

> 代码

```java
class Solution {
    int count = 0;
    int k;
    HashMap<Integer, Integer> h = new HashMap<>();
    public int pathSum(TreeNode root, int sum) {
        k = sum;
        preorder(root, 0);
        return count;
    }
    public void preorder(TreeNode node, int cur){
        if(node == null){
            return;
        }
        cur += node.val;
        if(cur == k){
            count++;
        }
        count += h.getOrDefault(cur - k, 0);
        h.put(cur, h.getOrDefault(cur, 0) + 1);
        preorder(node.left, cur);
        preorder(node.right, cur);
        h.put(cur, h.getOrDefault(cur, 0) - 1);
    }
}
```

> 复杂度分析

遍历树的节点，时间复杂度O(n)

额外使用map保存路径，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Path Sum III.

Memory Usage: 38.6 MB, less than 92.27% of Java online submissions for Path Sum III.
