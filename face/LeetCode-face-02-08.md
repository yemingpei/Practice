### LeetCode-face-02-08

> 题目链接

[LeetCode-face-02-08](https://leetcode-cn.com/problems/linked-list-cycle-lcci/)

> 思路

遍历链表，快慢指针在环内相遇，然后从相遇点出发，和头部出发，下个相遇点就是环的入口

> 代码

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode low = head;
        ListNode fast = head;
        while(fast !=null && fast.next != null){
            low = low.next;
            fast = fast.next.next;
            if(low == fast){
                ListNode node = head;
                while(node != low){
                    node = node.next;
                    low = low.next;
                }
                return node;
            }
        }
        return null;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用三个指针，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了97.59%的用户
