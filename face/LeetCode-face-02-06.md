### LeetCode-face-02-06

> 题目链接

[LeetCode-face-02-06](https://leetcode-cn.com/problems/palindrome-linked-list-lcci/)

> 思路

快慢指针找到中点，并反向记录数字，然后一一比较

> 代码

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        if(head == null) return true;
        ListNode heads = null;
        ListNode low = head;
        ListNode fast = head;
        while(fast.next != null){
            ListNode node = new ListNode(low.val);
            node.next = heads;
            heads = node;
            if(fast.next.next != null){
                fast = fast.next.next;
                low = low.next;
            }else fast = fast.next;
        }
        while(heads != null){
            low = low.next;
            if(heads.val != low.val) return false;
            heads = heads.next;
        }
        return true;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用一个链表辅助，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：42.1 MB, 在所有 Java 提交中击败了44.33%的用户
