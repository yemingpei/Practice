### LeetCode-443-String-Compression

> 题目链接

[LeetCode-443-String-Compression](https://leetcode.com/problems/string-compression/)

> 思路

遍历数组，然后计算可以压缩的值，计算int的位数的时候，同时完成int的转换，反转

> 代码

```java
class Solution {
    public int compress(char[] chars) {
        if(chars.length == 0) return 0;
        int count = 0;
        char s = chars[0];
        int number = 1;
        for(int i = 1; i < chars.length; i++){
            if(chars[i] == s) number++;
            else{
                count = count + intLength(number, chars, count, s) + 1;
                number = 1;
                s = chars[i];
            }
        }
        count = count + intLength(number, chars, count, s) + 1;
        return count;
    }
    public int intLength(int n, char[] chars, int start, char c){
        chars[start] = c;
        if(n == 1) return 0;
        int count = 0;
        while(n != 0){
            count++;
            chars[start + count] = (char)('0' + n % 10);
            n /= 10;
        }
        int s = start + 1;
        int e = start + count;
        while(e > s){
            char k = chars[s];
            chars[s] = chars[e];
            chars[e] = k;
            s++;
            e--;
        }
        return count;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

在原数组上操作，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for String Compression.

Memory Usage: 38.5 MB, less than 87.99% of Java online submissions for String Compression.
