### LeetCode-143-Reorder-List

> 题目链接

[LeetCode-143-Reorder-List](https://leetcode.com/problems/reorder-list/)

> 思路

先记录position和对应的node节点，然后首尾开始链接

> 代码

```java
class Solution {
    public void reorderList(ListNode head) {
        List<ListNode> list = new ArrayList<>();
        ListNode node = head;
        while(node != null){
            list.add(node);
            node = node.next;
        }
        if(list.size() > 2){
            node = list.get(0);
            int start = 1;
            int end = list.size() - 1;
            while(end >= start){
                node.next = list.get(end);
                node = node.next;
                end--;
                if(end < start) break;
                node.next = list.get(start);
                node = node.next;
                start++;
            }
            node.next = null;
        }
    }
}
```

> 复杂度分析

遍历了两遍链表，时间复杂度O(n)

额外使用ArrayList记录节点，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 97.64% of Java online submissions for Reorder List.

Memory Usage: 42 MB, less than 86.99% of Java online submissions for Reorder List.
