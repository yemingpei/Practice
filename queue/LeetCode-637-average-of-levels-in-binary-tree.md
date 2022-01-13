### LeetCode-637-average-of-levels-in-binary-tree

> 题目链接

[LeetCode-637-average-of-levels-in-binary-tree](https://leetcode-cn.com/problems/average-of-levels-in-binary-tree/)

> 思路

逐层遍历队列，然后计算每一层的平均值

> 代码

```java
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new LinkedList<>();
        if(root == null) return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while(!queue.isEmpty()){
            int size = queue.size();
            double sum = 0;
            for(int i = 0; i < size; i++){
                TreeNode node = queue.poll();
                sum += node .val;
                if(node.left != null) queue.offer(node.left);
                if(node.right != null) queue.offer(node.right);
            }
            result.add(sum / size);
        }
        return result;
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

额外使用队列，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了94.76%的用户

内存消耗：40.3 MB, 在所有 Java 提交中击败了57.24%的用户
