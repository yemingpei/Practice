### LeetCode-face-02-01

> 题目链接

[LeetCode-face-02-01](https://leetcode-cn.com/problems/remove-duplicate-node-lcci/)

> 思路

记录出现过的数据，用数组记录，如果出现过就跳过，否则就链接，最后要处理尾节点

> 代码

```java
class Solution {
    public ListNode removeDuplicateNodes(ListNode head) {
        boolean[] result = new boolean[20001];
        ListNode pre = new ListNode(0);
        pre.next = head;
        ListNode low = pre;
        ListNode fast = head;
        while(fast != null){
            if(!result[fast.val]){
                low.next = fast;
                low = low.next;
                result[fast.val] = true;
            }
            fast = fast.next;
        }
        low.next = null;
        return pre.next;
    }
}
```

> 复杂度分析

遍历链表，时间复杂度O(n)

额外使用长度为常数的数组，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：41.2 MB, 在所有 Java 提交中击败了5.07%的用户
