### LeetCode-face-04-09

> 题目链接

[LeetCode-face-04-09](https://leetcode-cn.com/problems/bst-sequences-lcci/)

> 思路

回溯法，利用list代替队列的作用，确保每层节点被依次添加，利用保存原数据和遍历越过之前的节点，达到跳过的效果。

> 代码

```java
class Solution {
    private List<List<Integer>> result;

    public List<List<Integer>> BSTSequences(TreeNode root) {
        result = new ArrayList<>();
        List<Integer> path = new ArrayList<>();
        if(root == null) {
            result.add(path);
            return result;
        }
        path.add(root.val);
        List<TreeNode> content = new LinkedList<>();
        if(root.left != null) content.add(root.left);
        if(root.right != null) content.add(root.right);
        dfs(content, path);
        return result;
    }

    private void dfs(List<TreeNode> content, List<Integer> path) {
        if(content.isEmpty()) {
            result.add(new ArrayList<>(path));
            return;
        }
        List<TreeNode> temp = new ArrayList<>(content);
        for(int i = 0; i < content.size(); i++) {
            TreeNode node = content.get(i);
            path.add(node.val);
            content.remove(i);
            if(node.left != null) content.add(node.left);
            if(node.right != null) content.add(node.right);
            dfs(content, path);
            path.remove(path.size() - 1);
            content = new ArrayList<>(temp);
        }
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(2 ^ logn) 

递归深度logn，空间复杂度O(nlogn)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了87.87%的用户

内存消耗：40.1 MB, 在所有 Java 提交中击败了80.00%的用户
