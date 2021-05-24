### LeetCode-offer-65

> 题目链接

[LeetCode-offer-65](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

> 思路

(a & b) << 1代表进位，a ^ b代表非进位的结果，运算至进位为0

> 代码

```java
class Solution {
    public int add(int a, int b) {
        int plus = (a & b) << 1;
        int sum = a ^ b;
        while(plus != 0){
            int number = (sum & plus) << 1;
            sum = sum ^ plus;
            plus = number;
        }
        return sum;
    }
}
```

> 复杂度分析

进位次数有限，时间复杂度O(1)

额外使用两个int来辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：34.8 MB, 在所有 Java 提交中击败了99.37%的用户
