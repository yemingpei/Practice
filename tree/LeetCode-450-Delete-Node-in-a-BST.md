### LeetCode-450-Delete-Node-in-a-BST

> 题目链接

[LeetCode-450-Delete-Node-in-a-BST](https://leetcode.com/problems/delete-node-in-a-bst/)

> 思路

先通过二叉搜索树的特性，找到要替换的点，然后不断寻找左子树换位，否则就是右子树，直到叶子结点

> 代码

```java
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root == null) return null;
        if(root.val < key) root.right = deleteNode(root.right, key);
        else if(root.val > key) root.left = deleteNode(root.left, key);
        else{
            if(root.left == null) return root.right;
            if(root.right == null) return root.left;
            TreeNode node = getLeftMax(root.left);
            root.val = node.val;
            root.left = deleteNode(root.left, node.val);
        }
        return root;
    }
    
    public TreeNode getLeftMax(TreeNode node){
        while(node != null && node.right != null){
            node = node.right;
        }   
        return node;
    }
}
```

> 复杂度分析

二叉搜索树遍历，时间复杂度O(logn)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Delete Node in a BST.

Memory Usage: 39.3 MB, less than 81.63% of Java online submissions for Delete Node in a BST.
