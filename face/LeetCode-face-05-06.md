### LeetCode-face-05-06

> 题目链接

[LeetCode-face-05-06](https://leetcode-cn.com/problems/convert-integer-lcci/)

> 思路

先进行异或，得到不同的位数，然后通过number & (number - 1)来计算1的个数

> 代码

```java
class Solution {
    public int convertInteger(int A, int B) {
        int number = A ^ B;
        int count = 0;
        while(number != 0){
            count++;
            number = number & (number - 1);
        }
        return count;
    }
}
```

> 复杂度分析

位运算，时间复杂度O(1) 

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.2 MB, 在所有 Java 提交中击败了56.69%的用户
