### LeetCode-429-N-ary-Tree-Level-Order-Traversal

> 题目链接

[LeetCode-429-N-ary-Tree-Level-Order-Traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)

> 思路

深度遍历树，利用深度为同一个数组的原理，一边遍历，一边添加，节省空间

> 代码

```java
class Solution {
    public List<List<Integer>> levelOrder(Node root) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(0, root, res);
        return res;
    }
    
    private void dfs(int depth, Node cur, List<List<Integer>> res) {
        if (cur == null)  return;
        if (res.size() == depth) res.add(new ArrayList<>());
        res.get(depth).add(cur.val);
        for (Node child : cur.children) dfs(depth + 1, child, res);
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

无使用额外变量t，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for N-ary Tree Level Order Traversal.

Memory Usage: 39.7 MB, less than 88.09% of Java online submissions for N-ary Tree Level Order Traversal.
