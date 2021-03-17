### LeetCode-offer-06

> 题目链接

[LeetCode-offer-06](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

> 思路

先遍历链表，计算数量，然后再遍历链表，设置数组的值

> 代码

```java
class Solution {
    public int[] reversePrint(ListNode head) {
        int count = 0;
        ListNode node = head;
        while(node != null){
            node = node.next;
            count++;
        }
        int[] result = new int[count];
        while(head != null){
            result[--count] = head.val;
            head = head.next;
        }
        return result;
    }
}
```

> 复杂度分析

遍历两遍链表，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了85.16%的用户
