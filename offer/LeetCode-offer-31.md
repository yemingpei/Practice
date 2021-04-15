### LeetCode-offer-31

> 题目链接

[LeetCode-offer-31](https://leetcode-cn.com/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/)

> 思路

比较pushed和popped，不相等就入栈，直到找到相等为止，然后看栈顶是否符合，符合就出栈，相同则跳过

> 代码

```java
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
        Node head = null;
        int position = 0;
        for(int i = 0; i < popped.length; i++){
            if(head != null && head.val == popped[i]){
                head = head.next;
                continue;
            }
            if(position == pushed.length) return false;
            if(popped[i] == pushed[position]) {
                position++;
                continue;
            }
            while(pushed[position] != popped[i]){
                head = new Node(pushed[position],head);
                position++;
                if(position == pushed.length) return false;
            }
            position++;
        }
        return true;
    }
    public class Node{
        int val;
        Node next;
        public Node(int val, Node next){
            this.val = val;
            this.next = next;
        }
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(n)

额外使用链表保存数据，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.02%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了33.74%的用户
