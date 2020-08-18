### LeetCode-125-Valid-Palindrome

> 题目链接

[LeetCode-125-Valid-Palindrome](https://leetcode.com/problems/valid-palindrome/)

> 思路

从两端往中间，一一比较，不相同则提前结束

> 代码

```java
class Solution {
    public boolean isPalindrome(String s) {
        int start = 0;
        int end = s.length() - 1;
        while(end > start){
            while(start < end && !Character.isLetterOrDigit(s.charAt(start)))
                start++;
            while(start < end && !Character.isLetterOrDigit(s.charAt(end)))
                end--;
            if(end == start) break;
            if(Character.toLowerCase(s.charAt(start)) != Character.toLowerCase(s.charAt(end))) return false;
            start++;
            end--;
        }
        return true;
    }
}
```

> 复杂度分析

从两端往中间遍历字符串，时间复杂度O(n)

额外使用int记录前后位置，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 97.83% of Java online submissions for Valid Palindrome.

Memory Usage: 39.5 MB, less than 87.45% of Java online submissions for Valid Palindrome.
