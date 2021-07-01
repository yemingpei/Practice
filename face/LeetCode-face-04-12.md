### LeetCode-face-04-12

> 题目链接

[LeetCode-face-04-12](https://leetcode-cn.com/problems/paths-with-sum-lcci/)

> 思路

双重递归，每个子节点是路径本身，又是起点。所以要使用双重递归，比较容易理解，当然可以通过记录过程中的情况来优化，避免重复计算

> 代码

```java
class Solution {

    public int pathSum(TreeNode root, int sum) {
        if(root == null) return 0;
        return pathSum(root.left, sum) + pathSum(root.right, sum) + checkSum(root, sum);
    }

    public int checkSum(TreeNode root, int sum){
        if(root == null) return 0;
        int result = root.val == sum ? 1 : 0;
        int number = sum - root.val;
        return result + checkSum(root.left, number) + checkSum(root.right, number);
    } 

}
```

> 复杂度分析

需要遍历树的节点，时间复杂度O(nlogn) 

递归深度logn，空间复杂度O(logn)

> 总结

执行用时：9 ms, 在所有 Java 提交中击败了63.54%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了93.72%的用户
