### LeetCode-face-04-02

> 题目链接

[LeetCode-face-04-02](https://leetcode-cn.com/problems/minimum-height-tree-lcci/)

> 思路

根据二叉树的特点，数组的中点为root，然后左右子树的数量就是相等的，或者相差1

> 代码

```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums.length == 0) return null;
        return getSortedNode(nums, 0, nums.length - 1);
    }
    public TreeNode getSortedNode(int[] nums, int start, int end){
        if(start == end) return new TreeNode(nums[start]);
        int mid = (end - start) / 2 + start;
        TreeNode node = new TreeNode(nums[mid]);
        if(start != mid) node.left = getSortedNode(nums, start, mid - 1);
        if(end != mid) node.right = getSortedNode(nums, mid + 1, end);
        return node;
    }
}
```

> 复杂度分析

需要遍历数组，时间复杂度O(n) 

递归栈深度logn，空间复杂度O(logn)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.8 MB, 在所有 Java 提交中击败了94.82%的用户
