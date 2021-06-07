### LeetCode-face-02-02

> 题目链接

[LeetCode-face-02-02](https://leetcode-cn.com/problems/kth-node-from-end-of-list-lcci/)

> 思路

快慢指针，当尾节点到达尾部，慢节点就是倒数第k个

> 代码

```java
class Solution {
    public int kthToLast(ListNode head, int k) {
        ListNode fast = head;
        for(int i = 0; i < k; i++){
            fast = fast.next;
        }
        ListNode low = head;
        while(fast != null){
            fast = fast.next;
            low = low.next;
        }
        return low.val;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用快慢两个节点，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36 MB, 在所有 Java 提交中击败了59.23%的用户
