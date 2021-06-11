### LeetCode-face-02-05

> 题目链接

[LeetCode-face-02-05](https://leetcode-cn.com/problems/sum-lists-lcci/)

> 思路

利用一个数字记录进位，然后开始拼接和，一直到两个链表都结束

> 代码

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int number = 0;
        ListNode head = new ListNode(0);
        ListNode node = head;
        while(l1 != null || l2 != null || number > 0){
            if(l1 != null){
                number += l1.val;
                l1 = l1.next;
            }
            if(l2 != null){
                number += l2.val;
                l2 = l2.next;
            }
            int num = number % 10;
            node.next = new ListNode(num);
            node = node.next;
            number = number / 10;
        }
        return head.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n + m)

额外使用一个链表辅助，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了76.77%的用户
