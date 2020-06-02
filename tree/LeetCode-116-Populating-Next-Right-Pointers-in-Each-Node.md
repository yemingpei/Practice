### LeetCode-116-Populating-Next-Right-Pointers-in-Each-Node

> 题目链接

[LeetCode-116-Populating-Next-Right-Pointers-in-Each-Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

> 思路

题目描述为完全二叉树，不会出现没有左子树，有右子树的情况，遍历树，递归赋值即可

> 代码

```java
class Solution {
    public Node connect(Node root) {
        if(root==null) return null;
        if(root.left!=null) root.left.next=root.right;
        if(root.right!=null) root.right.next= root.next!=null? root.next.left:null;
        connect(root.left);
        connect(root.right);
        return root;
    }
}
```

> 复杂度分析

遍历了整棵树，时间复杂度O(n)

无额外空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Populating Next Right Pointers in Each Node.

Memory Usage: 39.7 MB, less than 6.35% of Java online submissions for Populating Next Right Pointers in Each Node.
