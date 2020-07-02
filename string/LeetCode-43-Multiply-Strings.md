### LeetCode-43-Multiply-Strings

> 题目链接

[LeetCode-43-Multiply-Strings](https://leetcode.com/problems/multiply-strings/)

> 思路

通过加法竖式求和，每个数的每一位相乘，最后再进位，转为字符串

> 代码

```java
class Solution {
    public String multiply(String num1, String num2) {
        char[] s1 = num1.toCharArray();
        char[] s2 = num2.toCharArray();
        int M = s1.length, N = s2.length;
        int[] arr = new int[M + N];
        for (int i = M - 1; i >= 0; i--) {
            for (int j = N - 1; j >= 0; j--) {
                arr[i + j + 1] += (s1[i] - '0') * (s2[j] - '0');
            }
        }
        int carry = 0;
        for (int i = M + N - 1; i >= 0; i--) {
            int sum = carry + arr[i];
            arr[i] = sum % 10;
            carry = sum / 10;
        }
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < M + N; i++) {
            if (sb.length() > 0 || arr[i] != 0) {
                sb.append(arr[i]);
            }
        }
        return sb.length() == 0 ? "0" : sb.toString();
    }
}
```

> 复杂度分析

遍历两个字符串，时间复杂度O(m * n)

额外使用长度m + n的数组，空间复杂度O(m + n)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Multiply Strings.

Memory Usage: 39.3 MB, less than 77.43% of Java online submissions for Multiply Strings.
