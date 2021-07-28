### LeetCode-face-16-01

> 题目链接

[LeetCode-face-16-01](https://leetcode-cn.com/problems/swap-numbers-lcci/)

> 思路

位运算，使用三次异或，交换两个数字

> 代码

```java
class Solution {
    public int[] swapNumbers(int[] numbers) {
        numbers[0] = numbers[0] ^ numbers[1];
        numbers[1] = numbers[0] ^ numbers[1];
        numbers[0] = numbers[0] ^ numbers[1];
        return numbers;
    }
}
```

> 复杂度分析

使用异或的位运算，时间复杂度O(1)

无额外使用空间，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.5 MB, 在所有 Java 提交中击败了29.46%的用户
