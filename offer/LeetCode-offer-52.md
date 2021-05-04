### LeetCode-offer-52

> 题目链接

[LeetCode-offer-52](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

> 思路

遍历两个链表，观察是否相等，到达尾部时候，再交叉遍历

> 代码

```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode node1 = headA;
        ListNode node2 = headB;
        while(node1 != node2){
            if(node1 == null)
                node1 = headB;
            else
                node1 = node1.next;
            if(node2 == null)
                node2 = headA;
            else
                node2 = node2.next;
        }
        return node1;
    }
}
```

> 复杂度分析

循环两个链表两次，时间复杂度O(m + n)

额外使用指针来辅助，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：41 MB, 在所有 Java 提交中击败了92.87%的用户
