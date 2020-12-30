### LeetCode-357-Count-Numbers-with-Unique-Digits

> 题目链接

[LeetCode-357-Count-Numbers-with-Unique-Digits](https://leetcode.com/problems/count-numbers-with-unique-digits/)

> 思路

因为范围是[0,n)，所以每次增加一次10倍，就要增加当前i - 1位数字，然后第一位有9个选择，第二位有9个选择，第三位剩下8个选择，依次类推，则有求和公式sum = sum * number

> 代码

```java
class Solution {
    public int countNumbersWithUniqueDigits(int n) {
        if(n == 0) return 1;
        int result = 10, number = 9, sum = 9;
        for(int i = 1; i < n; i++){
            result += sum *= number--;
        }
        return result;
    }
}
```

> 复杂度分析

需要遍历一轮n，时间复杂度O(n)

需要int来表示结果，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Count Numbers with Unique Digits.

Memory Usage: 35.9 MB, less than 25.05% of Java online submissions for Count Numbers with Unique Digits.
