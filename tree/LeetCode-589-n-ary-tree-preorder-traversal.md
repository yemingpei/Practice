### LeetCode-589-n-ary-tree-preorder-traversal

> 题目链接

[LeetCode-589-n-ary-tree-preorder-traversal](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/)

> 思路

遍历整个树，先输出根，然后子节点逆序加入队列

> 代码

```java
class Solution {
    public List<Integer> preorder(Node root) {
        List<Integer> result = new ArrayList<>();
        if(root == null) return result;
        Stack<Node> stack = new Stack<>();
        stack.push(root);
        while(!stack.isEmpty()){
            Node node = stack.pop();
            result.add(node.val);
            if(node.children != null && !node.children.isEmpty()){
                for(int i = node.children.size() - 1; i >= 0; i--)
                    stack.push(node.children.get(i));
            }
        }
        return result;
    }
}
```

> 复杂度分析

遍历整个树，时间复杂度O(n)

额外使用stack，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了40.21%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了87.53%的用户
