### LeetCode-106-Construct-Binary-Tree-from-Inorder-and-Postorder-Traversal

> 题目链接

[LeetCode-106-Construct-Binary-Tree-from-Inorder-and-Postorder-Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

> 思路

思路同[LeetCode-105-Construct-Binary-Tree-from-Preorder-and-Inorder-Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)，只是后序遍历最后一个为根节点

> 代码

```java
class Solution {
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        if(postorder.length == 0) return null;
        Map<Integer,Integer> map = new HashMap<>();
        for(int i = 0; i < inorder.length; i++){
            map.put(inorder[i], i);
        }
        return getRootNode(map, postorder, 0, postorder.length - 1, inorder, 0, inorder.length - 1);
    }
    public TreeNode getRootNode(Map<Integer,Integer> map, int[] postorder, int poststart, int postend, int[] inorder, int instart, int inend){
        if(poststart == postend) return new TreeNode(postorder[postend]);
        int inRoot = map.get(postorder[postend]);
        int countLeft = inRoot - instart;
        int countRight = inend - inRoot;
        if(countLeft == 0)
            return new TreeNode(postorder[postend], null, getRootNode(map, postorder, poststart , postend - 1, inorder, instart + 1, inend));
        if(countRight == 0)
            return new TreeNode(postorder[postend], getRootNode(map, postorder, poststart, postend - 1, inorder, instart, inend - 1), null);
        return new TreeNode(postorder[postend], getRootNode(map, postorder, poststart, poststart + countLeft - 1, inorder, instart, inRoot - 1), getRootNode(map, postorder, poststart + countLeft, postend - 1, inorder, inRoot + 1, inend));
    }
}
```

> 复杂度分析

遍历了两遍数组 ，时间复杂度O(n)

map保存中序遍历的数据和位置，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 82.36% of Java online submissions for Construct Binary Tree from Inorder and Postorder Traversal.

Memory Usage: 42.3 MB, less than 5.40% of Java online submissions for Construct Binary Tree from Inorder and Postorder Traversal.
