### LeetCode-382-Linked-List-Random-Node

> 题目链接

[LeetCode-382-Linked-List-Random-Node](https://leetcode.com/problems/linked-list-random-node/)

> 思路

每个数都可以随机一遍都有相同的概率被抽到

> 代码

```java
class Solution {
    ListNode head;
    public Solution(ListNode head) {
        this.head = head;        
    }
    
    public int getRandom() {
        Random random = new Random();
        int index = 0;
        int count = 1;
        ListNode curr = head;
        while (curr != null) {
            if (random.nextInt(count) == 0)
                index = curr.val;
            count++;
            curr = curr.next;
        }
        return index;
    }
}
```

> 复杂度分析

遍历一遍链表，时间复杂度O(n)

额外使用两个辅助指针，空间复杂度O(1)

> 总结

Runtime: 15 ms, faster than 21.17% of Java online submissions for Linked List Random Node.

Memory Usage: 41.5 MB, less than 11.17% of Java online submissions for Linked List Random Node.
