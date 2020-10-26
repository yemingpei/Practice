### LeetCode-234-Palindrome-Linked-List

> 题目链接

[LeetCode-234-Palindrome-Linked-List](https://leetcode.com/problems/palindrome-linked-list/)

> 思路

用快慢指针找出中点，慢指针移动的同时，反转前面的链表，如果链表为单数，则需要跳过一个，然后一一比较

> 代码

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        ListNode fast = head, curr = head, prev = null;
        while(fast != null && fast.next != null) {
            fast = fast.next.next;
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        if(fast != null)
            curr = curr.next;
        while(prev != null) {
            if(curr.val != prev.val)return false;
            curr = curr.next;
            prev = prev.next;
        }
        return true;
    }
}
```

> 复杂度分析

遍历整个链表，时间复杂度O(n)

额外一个指针变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Palindrome Linked List.

Memory Usage: 41.2 MB, less than 5.04% of Java online submissions for Palindrome Linked List.
