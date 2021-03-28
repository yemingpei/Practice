### LeetCode-offer-15

> 题目链接

[LeetCode-offer-15](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)

> 思路

n & (n - 1)消除最左边的1，用这个方法来计算1的个数

> 代码

```java
public class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while(n != 0){
            count++;
            n = n & (n - 1);
        }
        return count;
    }
}
```

> 复杂度分析

最多32次，时间复杂度O(1)

额外使用int计数，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了96.87%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了62.07%的用户

