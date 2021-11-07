### LeetCode-515-find-largest-value-in-each-tree-row

> 题目链接

[LeetCode-515-find-largest-value-in-each-tree-row](https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/)

> 思路

广度遍历，寻找每一层最大的值

> 代码

```java
class Solution {
    public List<Integer> largestValues(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if(root == null) return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while(!queue.isEmpty()){
            int number = Integer.MIN_VALUE;
            int size = queue.size();
            for(int i = 0; i< size; i++){
                TreeNode node = queue.poll();
                number = Math.max(number, node.val);
                if(node.left != null) queue.offer(node.left);
                if(node.right != null) queue.offer(node.right);
            }
            result.add(number);
        }
        return result;
    }
}
```

> 复杂度分析

遍历全部节点，时间复杂度O(n)

额外使用队列，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了89.05%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了14.16%的用户
