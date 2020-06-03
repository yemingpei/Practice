### LeetCode-117-Populating-Next-Right-Pointers-in-Each-Node-II

> 题目链接

[LeetCode-117-Populating-Next-Right-Pointers-in-Each-Node-II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)

> 思路

递归分为四种情况：
1. 左右子树都为0，无需操作
2. 左子树为空，那右子树的next指向下一个节点的位置
3. 右子树为空，那左子树的next指向下一个节点的位置
4. 左子树的next指向右节点，右子树的next指向下一个节点的位置

寻找下个节点的位置，就是循环找到父亲的next的左子树或者右子树不为空，所以递归的方向必须是先右子树，再左子树

> 代码

```java
class Solution {
    public Node connect(Node root) {
        if(root == null) return null;
        if(root.left == null && root.right == null) return root;
        else if(root.left == null) root.right.next = findNextNode(root);
        else if(root.right == null) root.left.next = findNextNode(root);
        else{
            root.left.next = root.right;
            root.right.next = findNextNode(root);
        }
        connect(root.right);
        connect(root.left);
        return root;
    }
    
     public Node findNextNode(Node node){
        while(node.next != null){
            if(node.next.left != null) return node.next.left;
            if(node.next.right != null) return node.next.right;
            node=node.next;
        }
        return null;
    }
}
```

> 复杂度分析

遍历了整棵树，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Populating Next Right Pointers in Each Node II.

Memory Usage: 39.1 MB, less than 100.00% of Java online submissions for Populating Next Right Pointers in Each Node II.
