### LeetCode-504-base-7

> 题目链接

[LeetCode-504-base-7](https://leetcode-cn.com/problems/base-7/)

> 思路

不断模7，寻找对应的进制位数

> 代码

```java
class Solution {
    public String convertToBase7(int num) {
        return Integer.toString(num, 7);
    }
}
```

> 复杂度分析

不断除7，寻找转换位，时间复杂度O(logn)

无额外使用变量，空间复杂度O(·)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.8 MB, 在所有 Java 提交中击败了52.50%的用户
