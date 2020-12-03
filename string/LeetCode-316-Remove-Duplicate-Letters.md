### LeetCode-316-Remove-Duplicate-Letters

> 题目链接

[LeetCode-316-Remove-Duplicate-Letters](https://leetcode.com/problems/remove-duplicate-letters/)

> 思路
```java
"cbacdcbc"的演变流程为：
"c"（个数不唯一）
"b"(比前一个小，个数不唯一)
"a"(比前一个小，个数为1，锁定)
"ac"
"acd"(d个数为1，锁定)
"acdb"(c重复出现，不能进入)
```
用拼接字符代替stack来实现移除，减少时间的消耗

> 代码

```java
class Solution {
    public String removeDuplicateLetters(String s) {
        int[] frequency = new int[26];
        boolean[] visited = new boolean[26];
        char[] charArray = s.toCharArray();
        for (char ch: charArray) 
            frequency[ch - 'a']++;
        int index;
        StringBuilder str = new StringBuilder();
        for (char ch: charArray) {
            index = ch - 'a';
            frequency[index]--;
            if (visited[index])
                continue;
            while (str.length() > 0 && ch < str.charAt(str.length() - 1) && frequency[str.charAt(str.length() - 1) - 'a'] != 0) {
                visited[str.charAt(str.length() - 1) - 'a'] = false;
                str.deleteCharAt(str.length() - 1);
            }       
            str.append(ch);
            visited[index] = true;
        }     
        return str.toString();
    }
}
```

> 复杂度分析

遍历字符串，寻找下一个移除的值，不超过26，时间复杂度O(n)

额外使用数组长度都不超过26，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Remove Duplicate Letters.

Memory Usage: 37.4 MB, less than 98.40% of Java online submissions for Remove Duplicate Letters.
