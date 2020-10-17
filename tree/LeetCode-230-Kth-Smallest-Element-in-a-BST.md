### LeetCode-230-Kth-Smallest-Element-in-a-BST

> 题目链接

[LeetCode-230-Kth-Smallest-Element-in-a-BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

> 思路

利用递归进行中序遍历，找到k个就返回。

> 代码

```java
class Solution {
    private int i = 0;
    public int kthSmallest(TreeNode root, int k) {
        if(root == null) return 0;
        if(root.left != null) {
            int left = kthSmallest(root.left, k);
            if(i == k) return  left;
        }
        i++;
        if(i == k) return root.val;
        if(root.right != null) {
            int right = kthSmallest(root.right, k);
            if(i == k) return  right;
        }
        return 0;
    }
}
```

> 复杂度分析

需要遍历树的元素，时间复杂度O(n)

额外使用i来记录到了第几个数字，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Kth Smallest Element in a BST.

Memory Usage: 38.7 MB, less than 14.10% of Java online submissions for Kth Smallest Element in a BST.
