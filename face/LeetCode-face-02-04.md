### LeetCode-face-02-04

> 题目链接

[LeetCode-face-02-04](https://leetcode-cn.com/problems/partition-list-lcci/)

> 思路

先分成两段，一个比x小，另外就是就是第二段，最后拼接

> 代码

```java
class Solution {
    public ListNode partition(ListNode head, int x) {
        if(head == null) return head;
        ListNode first = new ListNode(0);
        ListNode second = new ListNode(0);
        ListNode node = first;
        ListNode node2 = second;
        while(head !=null){
            if(head.val < x) {
                node.next = head;
                node = node.next;
            }else{
                node2.next = head;
                node2 = node2.next;
            }
            head = head.next;
        }
        node2.next = null;
        node.next = second.next;
        return first.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用四个辅助节点，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.7 MB, 在所有 Java 提交中击败了67.38%的用户
