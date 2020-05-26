### LeetCode-104-Maximum-Depth-of-Binary-Tree

> 题目链接

[LeetCode-104-Maximum-Depth-of-Binary-Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

> 思路

遍历一遍树，节点不为null则加1，节点为null则和最大的深度比较，最后输出最大深度

> 代码

```java
class Solution {
    public int count;
    public int maxDepth(TreeNode root) {
        count = 0;
        depthTree(root,0);
        return count;
    }
    
    public void depthTree(TreeNode root,int number){
        if(root == null) count = Math.max(count,number);
        else{
            int depth = number + 1;
            depthTree(root.left, depth);
            depthTree(root.right, depth);
        }
    }
}
```

> 复杂度分析

需要遍历整个树的全部节点，时间复杂度O(n)

额外使用int 记录深度的最大值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Maximum Depth of Binary Tree.

Memory Usage: 39.4 MB, less than 89.79% of Java online submissions for Maximum Depth of Binary Tree.
