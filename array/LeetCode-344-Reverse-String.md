### LeetCode-344-Reverse-String

> 题目链接

[LeetCode-344-Reverse-String](https://leetcode.com/problems/reverse-string/)

> 思路

首尾指针交换位置，每次移动一步

> 代码

```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;
        while(right > left){
            char a = s[left];
            s[left] = s[right];
            s[right] = a;
            left++;
            right--;
        }
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要常量char保存临时变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 95.05% of Java online submissions for Reverse String.

Memory Usage: 45.6 MB, less than 76.70% of Java online submissions for Reverse String.
