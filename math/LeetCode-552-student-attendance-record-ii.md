### LeetCode-552-student-attendance-record-ii

> 题目链接

[LeetCode-552-student-attendance-record-ii](https://leetcode-cn.com/problems/student-attendance-record-ii/)

> 思路

p1 = p1 + p2 + p3; p4 = p4 + p5 + p6 + p1 + p2 + p3;p2 = p1;p3 = p2;p5 = p4;p6 = p5;计算可得

> 代码

```java
class Solution {
    public int checkRecord(int n) {
        long p1 = 1;
        long p2 = 1;
        long p3 = 0;
        long p4 = 1;
        long p5 = 0;
        long p6 = 0;
        for(int i = 1; i < n; i++){
            long number1 = p1;
            long number2 = p4;
            p1 = (p1 + p2 + p3) % 1000000007;
            p3 = p2;
            p2 = number1;
            p4 = (p4 + p5 + p6 + p1) % 1000000007;
            p6 = p5;
            p5 = number2;
        }
        return  (int)((p1 + p2 + p3 + p4 + p5 + p6) % 1000000007);
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n)

额外使用long计数，空间复杂度O(1)

> 总结

执行用时：19 ms, 在所有 Java 提交中击败了91.74%的用户

内存消耗：35.2 MB, 在所有 Java 提交中击败了95.87%的用户
