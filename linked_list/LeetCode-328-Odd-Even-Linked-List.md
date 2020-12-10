### LeetCode-328-Odd-Even-Linked-List

> 题目链接

[LeetCode-328-Odd-Even-Linked-List](https://leetcode.com/problems/odd-even-linked-list/)

> 思路

两个指针，分别记录单数和双数的节点，然后清楚双数的尾结点的指针，再链接起来

> 代码

```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        int count = 0;
        ListNode node = head;
        ListNode first = new ListNode();
        ListNode head2 = new ListNode();
        ListNode second = null;
        while(node != null){
            if(count % 2 == 0) {
                first.next = node;
                first = first.next;
            }else{
                if(second == null) {
                    second = node;
                    head2.next = second;
                }
                else {
                    second.next = node;
                    second = second.next;
                }
            }
            node = node.next;
            count++;
        }
        if(second != null) second.next = null;
        first.next = head2.next;
        return head;
    }
}
```

> 复杂度分析

遍历整个链表，时间复杂度O(n)

额外使用node记录指针，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Odd Even Linked List.

Memory Usage: 38.9 MB, less than 31.23% of Java online submissions for Odd Even Linked List.
