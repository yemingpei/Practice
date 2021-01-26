### LeetCode-415-Add-Strings

> 题目链接

[LeetCode-415-Add-Strings](https://leetcode.com/problems/add-strings/)

> 思路

模拟竖式的加法，但是要反转字符串，记录进位就可以了

> 代码

```java
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder result = new StringBuilder();
        int add = 0;
        int i = num1.length() - 1;
        int j = num2.length() - 1;
        while(i > -1 || j > -1){
            int a = i > -1? num1.charAt(i) - '0': 0;
            int b = j > -1? num2.charAt(j) - '0': 0;
            int number = a + b + add;
            add = number / 10;
            result.append(number % 10);
            i--;
            j--;
        }
        if(add != 0) result.append(add);
        return result.reverse().toString();
    }
}
```

> 复杂度分析

循环遍历完较长的字符串，时间复杂度O(m)

额外使用StringBuilder拼接字符，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 91.22% of Java online submissions for Add Strings.

Memory Usage: 38.9 MB, less than 85.34% of Java online submissions for Add Strings.
