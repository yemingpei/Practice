### LeetCode-590-n-ary-tree-postorder-traversal

> 题目链接

[LeetCode-590-n-ary-tree-postorder-traversal](https://leetcode-cn.com/problems/n-ary-tree-postorder-traversal/)

> 思路

遍历整个树，先输出根，然后子节点顺序加入队列

> 代码

```java
class Solution {
    public List<Integer> postorder(Node root) {
        LinkedList<Integer> result = new LinkedList<>();
        if(root == null) return result;
        Stack<Node> stack = new Stack<>();
        stack.push(root);
        while(!stack.isEmpty()){
            Node node = stack.pop();
            result.addFirst(node.val);
            if(node.children != null && !node.children.isEmpty())
                for(Node chail : node.children)
                    stack.push(chail);
        }
        return result;
    }
}
```

> 复杂度分析

遍历整个树，时间复杂度O(n)

额外使用stack，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了41.32%的用户

内存消耗：39.4 MB, 在所有 Java 提交中击败了22.56%的用户
