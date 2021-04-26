### LeetCode-offer-35

> 题目链接

[LeetCode-offer-35](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

> 思路

先遍历一遍链表，把链表构建出来，然后再遍历一次链表，构建他们的关系

> 代码

```java
class Solution {
    public Node copyRandomList(Node head) {
        if(head == null) return null;
        Map<Node,Node> map = new HashMap<Node, Node>();
        Node cur = head;
        while(cur != null){
            map.put(cur,new Node(cur.val));
            cur = cur.next;
        }
        cur = head;
        while(cur != null){
            map.get(cur).next = map.get(cur.next);
            map.get(cur).random = map.get(cur.random);
            cur = cur.next;
        }
        return map.get(head);
    }
}
```

> 复杂度分析

遍历两次链表，时间复杂度O(n)

额外使用map来保存节点，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了28.33%的用户
