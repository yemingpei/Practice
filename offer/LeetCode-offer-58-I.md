### LeetCode-offer-58-I

> 题目链接

[LeetCode-offer-58-I](https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

> 思路

从尾到头，开始寻找单词，然后拼接

> 代码

```java
class Solution {
    public String reverseWords(String s) {
        s = s.trim();
        int i = s.length() - 1, j = i;
        StringBuilder sb = new StringBuilder();
         while(i >= 0){
            while(i >= 0 && s.charAt(i) != ' ') i--;
            sb.append(s.substring(i + 1, j + 1) + " ");
            while(i >= 0 && s.charAt(i) == ' ') i--;
            j = i;
        }
        return sb.toString().trim();
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用两个int边界值标记窗口，空间复杂度O(1)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了69.24%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了40.67%的用户
