### LeetCode-offer-18

> 题目链接

[LeetCode-offer-18](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

> 思路

寻找对应的节点，然后进行删除，可能存在多个节点

> 代码

```java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        ListNode pre = new ListNode(0);
        pre.next = head;
        ListNode node = pre;
        while(node != null && node.next != null){
            if(node.next.val == val){
               node.next = node.next.next;
            }
            node = node.next;
        }
        return pre.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O( n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.9 MB, 在所有 Java 提交中击败了50.00%的用户
