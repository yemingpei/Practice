### LeetCode-61-Rotate-List

> 题目链接

[LeetCode-61-Rotate-List](https://leetcode.com/problems/rotate-list/)

> 思路

先寻找真正的k值，k%n，然后前后指针一起移动到链表尾部，然后进行一次链表移除，并插入到头部的操作

> 代码

```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null) return head;
        ListNode resultList = new ListNode(0);
        resultList.next = head;
        int count = 0;
        ListNode p = resultList;
        while (p.next != null && count < k) {
          p = p.next;
          count++;
        }
        if (count < k) {
          int realNum = k % count;
          p = resultList;
          for (int i = 0; i < realNum; i++) {
            p = p.next;
          }
        }
            if (p.next == null) return head;
        ListNode first = resultList;
        while(p.next != null){
          first = first.next;
          p = p.next;
        }
        p.next = resultList.next;
        resultList.next = first.next;
        first.next = null;
        return resultList.next;
    }
}
```

> 复杂度分析

先寻找第k个，最坏情况是k大于链表的长度，用时为n，然后有一个纠正的操作，用时为k，再走一遍链表，用时为n-k，整体用时最坏情况应该是2n，时间复杂度O(n)

额外使用3个辅助指针，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Rotate List.
Memory Usage: 39.2 MB, less than 41.38% of Java online submissions for Rotate List.
