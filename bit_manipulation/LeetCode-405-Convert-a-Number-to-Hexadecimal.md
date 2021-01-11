### LeetCode-405-Convert-a-Number-to-Hexadecimal

> 题目链接

[LeetCode-405-Convert-a-Number-to-Hexadecimal](https://leetcode.com/problems/convert-a-number-to-hexadecimal/)

> 思路

每次右移消去四位，转化成16进制的字符

> 代码

```java
class Solution {
    public String toHex(int num) {
        if(num==0) return "0";
        char[] map= new char[]{'0','1','2','3','4','5','6','7','8','9','a','b','c','d','e','f'};
        StringBuilder s= new StringBuilder();
        while(num != 0){
            s.append(map[num & 15]);
            num >>>= 4;
        }
        return s.reverse().toString();
    }
}
```

> 复杂度分析

使用位运算，最多进行8次，时间复杂度O(1)

额外使用长度为16的char数组，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Convert a Number to Hexadecimal.

Memory Usage: 38.2 MB, less than 6.25% of Java online submissions for Convert a Number to Hexadecimal.
