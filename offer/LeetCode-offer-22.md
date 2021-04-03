### LeetCode-offer-22

> 题目链接

[LeetCode-offer-22](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

> 思路

前后指针，一起移动，到链表尾部，则能找到倒数第k个

> 代码

```java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode node = head;
        ListNode pre = head;
        for(int i = 1; i < k; i++){
            node = node.next;
        }
        while(node.next != null){
            node = node.next;
            pre = pre.next;
        }
        return pre;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用二个指针，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.1 MB, 在所有 Java 提交中击败了83.84%的用户
