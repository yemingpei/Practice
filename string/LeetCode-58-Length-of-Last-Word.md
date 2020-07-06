### LeetCode-58-Length-of-Last-Word

> 题目链接

[LeetCode-58-Length-of-Last-Word](https://leetcode.com/problems/length-of-last-word/)

> 思路

从右往左遍历，先跳过空格，找到右边界，再从右边界开始寻找左边界

> 代码

```java
class Solution {
    public int lengthOfLastWord(String s) {
        int end = s.length() - 1;
        for(int i = s.length() - 1; i >= 0; i--){
            if(s.charAt(i) == ' ') end--;
            else break;
        }
        if(end < 0) return 0;
        int start = end;
        while(start >= 0){
            if(s.charAt(start) != ' ') start--;
            else break;
        }
        return end - start;
    }
}
```

> 复杂度分析

从右往左遍历字符串，时间复杂度O(n)

额外使用两个int来记录头和尾，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Length of Last Word.

Memory Usage: 37.1 MB, less than 99.10% of Java online submissions for Length of Last Word.
