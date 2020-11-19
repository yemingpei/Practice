### LeetCode-299-Bulls-and-Cows

> 题目链接

[LeetCode-299-Bulls-and-Cows](https://leetcode.com/problems/bulls-and-cows/)

> 思路

遍历字符串，比较是否字串位置相等，记录bulls，通过数字计数器来计算相同的数字个数cows

> 代码

```java
class Solution {
    public String getHint(String secret, String guess) {
        int[] digits = new int[10];
        int bulls = 0;
        int cows = 0;
        for(char c : secret.toCharArray()) {
            digits[c - '0']++;
        }
        for(int i =0; i < secret.length(); i++) {
            if(digits[guess.charAt(i) - '0']-- > 0)
                cows++;
            if (guess.charAt(i) == secret.charAt(i))
                bulls++;
        }
        StringBuilder result = new StringBuilder();
        result.append(bulls).append("A").append(cows - bulls).append("B");
        return result.toString();
    }
}
```

> 复杂度分析

循环遍历两个字符串，时间复杂度O(n)

额外使用长度为10的数组记录数字，两个int值来保存结果，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Bulls and Cows.

Memory Usage: 37.4 MB, less than 98.76% of Java online submissions for Bulls and Cows.
