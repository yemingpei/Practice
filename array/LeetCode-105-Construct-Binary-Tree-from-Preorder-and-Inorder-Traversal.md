### LeetCode-105-Construct-Binary-Tree-from-Preorder-and-Inorder-Traversal

> 题目链接

[LeetCode-105-Construct-Binary-Tree-from-Preorder-and-Inorder-Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

> 思路

前序遍历，第一个肯定是根节点，中序遍历，根节点所在位置前面的部分为左子树，后面部分为右子树，每次寻找到父节点，然后计算对应子树前序遍历和中序遍历的位置

> 代码

```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length == 0) return null;
        Map<Integer,Integer> map = new HashMap<>();
        for(int i = 0; i < inorder.length; i++){
            map.put(inorder[i], i);
        }
        return getRootNode(map, preorder, 0, preorder.length - 1, inorder, 0, inorder.length - 1);
    }
    public TreeNode getRootNode(Map<Integer,Integer> map, int[] preorder, int prestart, int preend, int[] inorder, int instart, int inend){
        if(prestart == preend) return new TreeNode(preorder[prestart]);
        int inRoot = map.get(preorder[prestart]);
        int countLeft = inRoot - instart;
        int countRight = inend - inRoot;
        if(countLeft == 0)
            return new TreeNode(preorder[prestart], null, getRootNode(map, preorder, prestart + 1, preend, inorder, instart + 1, inend));
        if(countRight == 0)
            return new TreeNode(preorder[prestart], getRootNode(map, preorder, prestart + 1, preend, inorder, instart, inend - 1), null);
        return new TreeNode(preorder[prestart], getRootNode(map, preorder, prestart + 1, prestart + countLeft, inorder, instart, inRoot - 1), getRootNode(map, preorder, prestart + countLeft + 1, preend, inorder, inRoot + 1, inend));
    }
}
```

> 复杂度分析

遍历了两遍数组 ，时间复杂度O(n)

map保存中序遍历的数据和位置，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 82.36% of Java online submissions for Construct Binary Tree from Preorder and Inorder Traversal.

Memory Usage: 40.4 MB, less than 5.27% of Java online submissions for Construct Binary Tree from Preorder and Inorder Traversal.
