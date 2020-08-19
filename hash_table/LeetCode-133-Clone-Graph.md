### LeetCode-133-Clone-Graph

> 题目链接

[LeetCode-133-Clone-Graph](https://leetcode.com/problems/clone-graph/)

> 思路

HashMap先记录node值，val是唯一值，若相同，则直接取出返回，避免重复操作

> 代码

```java
class Solution {
    public Node cloneGraph(Node node) {
        if(node == null) return null;
        Map<Integer,Node> map = new HashMap<>();
        return cloneNode(node, map);
    }
    public Node cloneNode(Node node, Map<Integer,Node> map){
        if(map.containsKey(node.val)) return map.get(node.val);
        Node result = new Node(node.val);
        map.put(node.val, result);
        for(int i = 0; i < node.neighbors.size(); i++)
            result.neighbors.add(cloneNode(node.neighbors.get(i), map));
        return result;
    }
}
```

> 复杂度分析

遍历了整个无向图，时间复杂度O(n)

额外使用了HashMap,空间复杂度O(n)

> 总结

Runtime: 26 ms, faster than 97.02% of Java online submissions for Clone Graph.

Memory Usage: 39.3 MB, less than 94.99% of Java online submissions for Clone Graph.
