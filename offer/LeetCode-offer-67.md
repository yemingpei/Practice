### LeetCode-offer-67

> 题目链接

[LeetCode-offer-67](https://leetcode-cn.com/problems/ba-zi-fu-chuan-zhuan-huan-cheng-zheng-shu-lcof/)

> 思路

先确定起始位置，然后就是记住正负号，用Integer.MAX_VALUE / 10来与判断是否溢出

> 代码

```java
class Solution {
    public int strToInt(String str) {
        int res = 0, bndry = Integer.MAX_VALUE / 10;
        int i = 0, sign = 1, length = str.length();
        if(length == 0) return 0;
        while(str.charAt(i) == ' ')
            if(++i == length) return 0;
        if(str.charAt(i) == '-') sign = -1;
        if(str.charAt(i) == '-' || str.charAt(i) == '+') i++;
        for(int j = i; j < length; j++) {
            if(str.charAt(j) < '0' || str.charAt(j) > '9') break;
            if(res > bndry || res == bndry && str.charAt(j) > '7')
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            res = res * 10 + (str.charAt(j) - '0');
        }
        return sign * res;
    }
}
```

> 复杂度分析

遍历了字符串，时间复杂度O(n)

额外使用五个int来辅助，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.41%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了83.46%的用户
