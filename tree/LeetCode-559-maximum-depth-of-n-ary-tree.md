### LeetCode-559-maximum-depth-of-n-ary-tree

> 题目链接

[LeetCode-559-maximum-depth-of-n-ary-tree](https://leetcode-cn.com/problems/maximum-depth-of-n-ary-tree/)

> 思路

依次返回每一层的高度，使用递归

> 代码

```java
class Solution {
    public int maxDepth(Node root) {
        if(root == null) return 0;
        if(root.children == null || root.children.isEmpty()) return 1;
        int max = 0;
        for(int i = 0; i < root.children.size(); i++){
            max = Math.max(max, maxDepth(root.children.get(i)));
        }
        return max + 1;
    }
}
```

> 复杂度分析

遍历树的每一个节点，时间复杂度O(n)

额外使用函数栈，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38 MB, 在所有 Java 提交中击败了99.48%的用户
