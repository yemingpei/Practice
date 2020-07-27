### LeetCode-108-Convert-Sorted-Array-to-Binary-Search-Tree

> 题目链接

[LeetCode-108-Convert-Sorted-Array-to-Binary-Search-Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

> 思路

数组是有序的，形成平衡树，那么数组就是中序遍历的结果，因为要保持高度平衡，那么root的位置必然在中心位置，利用递归，不断寻找中心点作为root，最终得到结果树

> 代码

```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        return getRootNode(0, nums.length - 1, nums);
    }
    public TreeNode getRootNode(int left, int right, int[] nums){
        if(left > right) return null;
        int mid = (left + right) >> 1;
        return new TreeNode(nums[mid], getRootNode(left, mid - 1, nums), getRootNode(mid + 1, right, nums));
    }
}
```

> 复杂度分析

需要遍历整个数组，时间复杂度O(n)

无额外空间使用，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Convert Sorted Array to Binary Search Tree.

Memory Usage: 39.6 MB, less than 24.89% of Java online submissions for Convert Sorted Array to Binary Search Tree.
