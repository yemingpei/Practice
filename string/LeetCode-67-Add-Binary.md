### LeetCode-67-Add-Binary

> 题目链接

[LeetCode-67-Add-Binary](https://leetcode.com/problems/add-binary/)

> 思路

模拟加法相加，注意进位的处理

> 代码

```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder ans = new StringBuilder();
        int i = a.length() - 1, j = b.length() - 1;
        int carry = 0;
        while(i >= 0 || j >= 0){
            int sum = carry;
            if(i >= 0)
                sum += a.charAt(i--) - '0';
            if(j >= 0)
                sum += b.charAt(j--) - '0';
            ans.append(sum % 2);
            carry = sum / 2;
        }
        if(carry == 1)
            ans.append(1);
        return ans.reverse().toString();
    }
}
```

> 复杂度分析

遍历两次最长的字符长度，时间复杂度O(n)

额外使用int来辅助标记，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 79.98% of Java online submissions for Add Binary.

Memory Usage: 39.8 MB, less than 20.14% of Java online submissions for Add Binary.
