### LeetCode-face-04-05

> 题目链接

[LeetCode-face-04-05](https://leetcode-cn.com/problems/legal-binary-search-tree-lcci/)

> 思路

从子节点开始比较，根据左子树都比根节点小，右子树比根节点大的特性，用递归完成，剪枝提前结束

> 代码

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        return isValidTree(root, null, null);
    }
    public boolean isValidTree(TreeNode root, Integer low, Integer hight){
        if(root == null) return true;
        if(low != null && low >= root.val) return false;
        if(hight != null && hight <= root.val) return false;
        return isValidTree(root.left, low, root.val) && isValidTree(root.right, root.val, hight);
    }
}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(n) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了52.45%的用户
