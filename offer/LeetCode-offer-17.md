### LeetCode-offer-17

> 题目链接

[LeetCode-offer-17](https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

> 思路

逐个打印数据

> 代码

```java
class Solution {
    public int[] printNumbers(int n) {
        int max = (int) Math.pow(10, n) - 1;
        int[] result = new int[max];
        for(int i = 0; i < max; i++) {
            result[i] = i + 1;
        }
        return result;
    }
}
```

> 复杂度分析

有多少个数字就打印多少次，时间复杂度O(10 ^ n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：46.8 MB, 在所有 Java 提交中击败了43.76%的用户
