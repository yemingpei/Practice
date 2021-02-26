### LeetCode-427-Construct-Quad-Tree

> 题目链接

[LeetCode-427-Construct-Quad-Tree](https://leetcode.com/problems/construct-quad-tree/)

> 思路

递归，先从最小的节点开始构造，判断四个子节点，最后才构造val和isLeaf

> 代码

```java
class Solution {
    public Node construct(int[][] grid) {
        return constructTree(grid, 0, 0, grid.length);   
    }
    
    public Node constructTree(int[][] grid, int x, int y, int len){
        if(len == 1)
            return new Node(grid[x][y] == 1, true, null, null, null, null);
        
        Node node = new Node();
        Node topLeft = constructTree(grid, x, y, len/2);
        Node topRight = constructTree(grid, x, y + len/2, len/2);
        Node bottomLeft = constructTree(grid, x + len/2, y, len/2);
        Node bottomRight = constructTree(grid, x+ len/2, y +len/2, len/2);
        if(topLeft.isLeaf && topRight.isLeaf && bottomLeft.isLeaf && bottomRight.isLeaf && topLeft.val == topRight.val && topRight.val == bottomLeft.val && bottomLeft.val == bottomRight.val){
            node.val = topLeft.val;
            node.isLeaf = true;
        }
        else{
        node.topLeft = topLeft;
        node.topRight = topRight;
        node.bottomLeft = bottomLeft;
        node.bottomRight = bottomRight;
        }
    return node;
    }
}
```

> 复杂度分析

递归不断组成四叉树，时间复杂度O(n)

递归层数为logn，空间复杂度O(logn)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Construct Quad Tree.

Memory Usage: 39.2 MB, less than 65.28% of Java online submissions for Construct Quad Tree.
