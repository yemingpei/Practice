### LeetCode-face-05-02

> 题目链接

[LeetCode-face-05-02](https://leetcode-cn.com/problems/bianry-number-to-string-lcci/)

> 思路

不断乘以2，看个位数就知道小数的下个进位是什么，不超过30次操作，到0.0就结束

> 代码

```java
class Solution {
    public String printBin(double num) {
        StringBuilder sb = new StringBuilder("0.");
        for(int i = 0; i < 30; i++){
            if(Double.compare(num, 0.0) == 0) return sb.toString();
            num *= 2;
            int number = (int)num;
            sb.append(number);
            num -= number;
        }
        return "ERROR";
    }
}
```

> 复杂度分析

最多30次运算，时间复杂度O(1) 

额外使用StringBuilder常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.6 MB, 在所有 Java 提交中击败了66.03%的用户
