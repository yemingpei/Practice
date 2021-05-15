### LeetCode-offer-58-II

> 题目链接

[LeetCode-offer-58-II](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

> 思路

拼接字符串，先分成两段，然后再进行拼接

> 代码

```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        StringBuilder sb = new StringBuilder();
        sb.append(s.substring(n, s.length()));
        sb.append(s.substring(0, n));
        return sb.toString();
    }
}
```

> 复杂度分析

截取数组再拼接，时间复杂度O(n)

额外使用StringBuilder拼接，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了32.63%的用户
