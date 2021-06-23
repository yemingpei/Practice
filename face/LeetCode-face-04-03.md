### LeetCode-face-04-03

> 题目链接

[LeetCode-face-04-03](https://leetcode-cn.com/problems/list-of-depth-lcci/)

> 思路

根据先根节点，然后右节点，接着左节点的方式，不断往子节点插入头节点。

> 代码

```java
class Solution {
    public ListNode[] listOfDepth(TreeNode tree) {
        List<ListNode> list = new LinkedList<>();
        if(tree != null) createNode(list, 0, tree);
        ListNode[] result = new ListNode[list.size()];
        list.toArray(result);
        return result;
    }
    public void createNode(List<ListNode> list, int height, TreeNode node){
        if(list.size() == height) list.add(new ListNode(node.val));
        else {
            ListNode pre = new ListNode(list.get(height).val);
            pre.next = list.get(height).next;
            list.get(height).val = node.val;
            list.get(height).next = pre;
        }
        if(node.right != null) createNode(list, height + 1, node.right);
        if(node.left != null) createNode(list, height + 1, node.left);
    }
}
```

> 复杂度分析

需要遍历全部树的节点，时间复杂度O(n) 

额外使用数组，空间复杂度O(logn)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了97.64%的用户

内存消耗：37 MB, 在所有 Java 提交中击败了22.92%的用户
